---
title: "Need suggestion about VNC in Linux server"
date: 2011-06-14
forum: Server Platforms
---

### Post by l1l143 on 2011-06-14
Hello,
I am a very newbie to Linux server and webhosting. 
I have four 4 dedicated IPs in my server, out of those 3 runing with different websites. But problem is all 3 having vnc access to my root, incase of main server having different IP to access. I want only one IP which is main server IP can access server through vnc and WHM panel, and all other IPs access will be limited to cpanel access. How to do it, please someone help me.

Thanks is advance.

---

### Post by HermanAB on 2011-06-14
Howdy,

VNC is mostly a Windows thing.  On Linux, VNC is almost always the wrong solution, because it is insecure and it is also hard to get to work.  SSH is the right solution and it is secure and very easy to get to work.

So, read the Snail Book and install SSH:
[http://www.snailbook.com](http://www.snailbook.com)

---

### Post by GDR! on 2011-06-14
While it's hard to disagree with HermanAB about the fact SSH tunnel would be better for your use case, it's a cool thing to have a remote VNC machine. vnc4server provides a package with a VNC server, use man vnc4server after installing it to learn how to use it.

---

