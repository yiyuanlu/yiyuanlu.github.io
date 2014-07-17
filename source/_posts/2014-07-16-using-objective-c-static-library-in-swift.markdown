---
layout: post
title: "在Swift中调用Objective-C的静态库"
date: 2014-07-16 16:17:57 +0800
comments: true
categories: [Swift，Objective-C，Static Library]
---

在Swift中调用Objective-C的静态库和调用Objective-C的源码方法基本一致，大致分为两个步骤：

#### 1.设定：`XXX-Bridging-Header.h`   

将静态库的头文件`import`进去，如图：

{% img center /images/blogimage/20140716/1.png %}


#### 2.调用静态库中的方法  

具体调用就不需要import Objective-C的头文件了(`XXX-Bridging-Header.h`中的import是全局的)，**<font color = "red">直接在Swift中使用Swift的语法调用Objective-C的静态库就可以了</font>**，如图：

{% img center /images/blogimage/20140716/2.png %}

####另：和直接调用Objective-C源码不一样的地方是：

#####A.Objective-C的源码拖进XCode，XCode会自动产生一个Objective-C与Swift桥接的头文件`XXX-Bridging-Header.h`（一个工程一个，XXX便是你的工程名），如图：

{% img center /images/blogimage/20140716/3.png %}

#####B.而Objective-C的静态库需要你自己产生这个头文件，而且需要加到XCode的`Build Settings`中的`Objective-C Bridging Header`.如图:

{% img center /images/blogimage/20140716/4.png %}

####坑：
1.目前遇到在静态库中使用`Notifycation Center`监听 `Active`和`Terminate`都未起作用

####总结：

看了官方的文档，双方混合调用都很方便，但是实际使用中肯定存在诸如上述的`坑`，个人建议大家慢慢将项目整体迁移至Swift，直接抛弃7.0一下的系统就好.

####参考：
[Swift Programming Language](https://developer.apple.com/library/prerelease/ios/documentation/swift/conceptual/swift_programming_language/index.html)  
[Using Swift with Cocoa and Objective-C](https://developer.apple.com/library/prerelease/ios/documentation/Swift/Conceptual/BuildingCocoaApps/index.html#//apple_ref/doc/uid/TP40014216)

<!-- more -->
