---
title: "System Recovery Help!!!"
date: 2008-11-24
forum: Server Platforms
---

### Post by drums907 on 2008-11-24
My 8.04 Server Crashed.  The Hard-disk controller failed.  After replacing the controller, I can't get the system to boot.  It sees the drives, but has a problem with booting up.  I keep getting the message.

Grub 1.5 Loading, please wait...
Error 15

I can't seem to find any information about "Error 15".  Using the 8.04 install disk I can get to a prompt in recovery console but I am completely lost at this point.  What is the source of my problem?  What must I do to correct it?

Thanks for any help!

---

### Post by ndefontenay on 2008-11-24
Can you find the logs of your server? It will give you more information about what's going on.

It should be located in /var/log

We should be able to give you more help when we know more.

Nico

---

### Post by ndefontenay on 2008-11-24
Hi.

I've found this thread for you:

[http://forum.gobolinux.org/discussion/78/grub-loading-error-15-solved/](http://forum.gobolinux.org/discussion/78/grub-loading-error-15-solved/)

Apparently a parameter is missing. You should go through what they talk about. There's a lot in there.

Nico

---

### Post by drums907 on 2008-11-24
Unfortunately, I can't seem to get there.  I am very new to Ubuntu and Linux in General.  I got the server working and have put a "LOT" of data on it.  However, I know relatively little about working behind the scenes.

I have a console running from the CD image.  I know I need to mount the partitions but I am not having any luck in doing this.

---

