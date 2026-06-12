---
title: "ideas for problem with ltsp"
date: 2005-12-05
forum: Server Platforms
---

### Post by ugus on 2005-12-05
hey all

i put a 5.10 with the ltsp client, everything was going well, until i used REALLY old thin clients, pentium200 didnt started x ,stuff like that, even with a pentium 3 the video gave me nomore than 640x480, but the k12 linux distro is almost transparent, had no problem with that, do i have to replace some Xfree86 or Xorg files?

---

### Post by UbuntUser4389 on 2005-12-06
I am glad I am not the only person having problems setting up a linux terminal server using Ubuntu. I am also using version 5.10 and I have been having a ton of problems setting it up. Ubuntu itself is very easy to use, but the LTSP software needs to have some work done on it.

I am sorry Ugus that I cannot help you out with your problem. It seems that there aren't that many people that have tried to set up a linux terminal server using Ubuntu. I haven't had much help on these forums either. I have looked/searched online and there isn't much help there as far as I've seen.

If Ubuntu isn't working for you but K12 is, continue using K12. 

Good Luck.

---

### Post by bluefrog on 2005-12-06
my ltsp server on ubuntu doesn't give me more problems than what I had with FC4. Now my clients are not very old...

If you want good hardware recognition than you should try edubuntu. It lacks the sound capacity and is a wee bit long to boot a client though. That will be corrected in the next release.

James

---

### Post by ugus on 2005-12-06
well, ok, i'll stick to fedora....

---

### Post by cactus on 2005-12-06
you know..i had all kinds of trouble with an ltsp setup that i had..
i moved to pxes..and... 
lets just say..i never looked back.
[http://www.2x.com/pxes/](http://www.2x.com/pxes/)

---

### Post by lebarjack on 2005-12-07
[QUOTE=ugus]do i have to replace some Xfree86 or Xorg files?[/QUOTE]
After reading the /opt/ltsp/i386/etc/init.d/ltsp-client-setup, it seems that X is reconfigured at boot time.
Have you tried to override the display resolution by editing the /opt/ltsp/i386/etc/lts.conf
see [here]("http://wiki.ltsp.org/twiki/bin/view/Ltsp/LtsConf#X_MODE_0_through_X_MODE_2")

---

### Post by lebarjack on 2005-12-07
There is some useful informations in this thread [http://ubuntuforums.org/showthread.php?t=91230]("http://ubuntuforums.org/showthread.php?t=91230")

---

