---
title: "Wubbi, Ubuntu and Virus/Spyware"
date: 2009-04-04
forum: Security
---

### Post by aml1648 on 2009-04-04
Since Wubi installs Ubuntu inside a Folder within the windows environment, it is effectively treating Ubuntu like just another windows based applicaiton, like Microsoft Office or a video game. You can uninstall Ubuntu from control panel like you would with any other applicaiton.

So, if someone catches a "made for windows" virus/spyware while running Ubuntu, e.g. while downloading infected files off Limewire, the virus will be placed in the same partition as windows os. 

As such, will the virus be able be to infect/damage the windows os? 

Furthermore, since Ubuntu does not have real time anti-virus&anti-spyware softwares running in the background, it seems that, given the same (reckless)browsing/downloading behavior, a user is much more likely to catch virus or malwares running Ubuntu this way than running windows.

Please let me know if my understanding is correct. Many Thanks!

---

### Post by bodhi.zazen on 2009-04-04
No, your understanding of wubi is incorrect. wubi is not a windows program, it is a ubuntu install from within windows and a virtual disk image mounted on lo.

See :

[http://www.goodbye-windows.com/downloads/mirrors/cutlersoftware.com/ubuntusetup/wubi/old/faq.html](http://www.goodbye-windows.com/downloads/mirrors/cutlersoftware.com/ubuntusetup/wubi/old/faq.html)

and 

[http://wubi-installer.org/faq.php](http://wubi-installer.org/faq.php)

---

### Post by albinootje on 2009-04-04
> **aml1648 said:**
>  Furthermore, since Ubuntu does not have real time anti-virus&anti-spyware softwares running in the background, it seems that, given the same (reckless)browsing/downloading behavior, a user is much more likely to catch virus or malwares running Ubuntu this way than running windows.
Having infections because of viruses in Linux is unlikely, see here : [https://help.ubuntu.com/community/Linuxvirus](https://help.ubuntu.com/community/Linuxvirus)

Trojan horses in Linux are possible, and of course there's problems like flash cookies, and click-jacking while browsing the web.

See here : 
[http://www.linuxplanet.com/linuxplanet/reports/6711/1/](http://www.linuxplanet.com/linuxplanet/reports/6711/1/)
[http://en.wikipedia.org/wiki/Clickjacking](http://en.wikipedia.org/wiki/Clickjacking)

Personally I like using the noscript addon in Firefox to minimize security problems through the web browser, but noscript has a bit of a "learning curve" before getting used to it.

---

