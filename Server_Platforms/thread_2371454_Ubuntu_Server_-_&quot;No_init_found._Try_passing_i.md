---
title: "Ubuntu Server - &quot;No init found. Try passing init=bootarg&quot; at the login"
date: 2017-09-14
forum: Server Platforms
---

### Post by inirocis on 2017-09-14
Hi to all!

I have a problem at the start of my Ubuntu Server 16.04.1.

When I restart my server I have the error:
```
run-init; /sbin/init: No such file or directory
Target filesystem doesn't have requested /sbin/init.
run-init: /sbin/init: No such file or directory
run-int: /etc/init: No such file or directory
run-init: /bin/sh: No such file or directory
run-init: No such file or directory
No init found. Try passing init=bootarg.
```
And can start the server.

My fdisk output is this: [https://i.imgur.com/GaxjLKA.png](https://i.imgur.com/GaxjLKA.png)
In sda6 I have /boot and in sda1 I have /.

How can I resolve this problem? Can you help me?

Thanks so much.
I tried to flag as bootable sda1 and then sda6 but I have always the same error.

---

### Post by deadflowr on 2017-09-14
How fresh an install is it?
If possible, reinstall a supported release such as 16.04 or 17.04 (though 17.04 has a very short life and will require a reinstall or upgrade to 17.10 around January.)
Basically you will be better off in the long run, since 16.10 is well beyond it's own end of life and so it'll probably keep having issues.

---

### Post by inirocis on 2017-09-14
hi [COLOR=#000000]deadflowr, thanks.
Unfortunately I need the 16.04.01 because I have an application that need this version. So I can't update it.


[/COLOR]

---

### Post by deadflowr on 2017-09-14
> **inirocis said:**
> hi [COLOR=#000000]deadflowr, thanks.
Unfortunately I need the 16.04.01 because I have an application that need this version. So I can't update it.


[/COLOR]

Which is the install 16.04 or 16.10?

---

### Post by inirocis on 2017-09-14
16.04.1. Sorry I had corrected it.

---

### Post by inirocis on 2017-09-15
My sda schema and /sda1 content is:
[img]https://i.imgur.com/w0Wryyo.png[/img]
The /boot folder is empty.
The boot partition is sda6.
[img]https://i.imgur.com/N298cy2.png[/img]


What can be the boot partition? sda1 or sda2? 

Have you some help for me?

Thanks so much!

---

