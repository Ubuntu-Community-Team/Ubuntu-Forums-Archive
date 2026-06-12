---
title: "Ubuntu Success story !"
date: 2005-10-27
forum: Testimonials &amp; Experiences
---

### Post by jvictor on 2005-10-27
These were the problems i faced with Ubuntu



My DVD writer SONY DRU810-A dint work & installed failed
Gaim dint work
Apt dint work properly

[http://ubuntuforums.org/showthread.php?t=77219](http://ubuntuforums.org/showthread.php?t=77219)
[http://ubuntuforums.org/showthread.php?t=76716](http://ubuntuforums.org/showthread.php?t=76716)
[http://ubuntuforums.org/showthread.php?t=76354](http://ubuntuforums.org/showthread.php?t=76354)
[http://ubuntuforums.org/showthread.php?t=63236](http://ubuntuforums.org/showthread.php?t=63236)


The solutions are

Had to enable DMA on the DVD+RW. 

I used to have probs while installing bcoz the dvd drive stalled half way , and gave me an error msg bad MD5 ! 

How i  solved this was, boot in from the cd rom, and at the first screen, go to the shell ctl+alt+f2 & enable DMA using hdparm -d1 /dev/hdc, now the install & dvd writing works fine using nautilus, Gnome baker segfaults still.. 

Gaim couldnt connect to any service , The issue is that it doesnt like the server name eg.scs.msg.yahoo.com but we need to give the servers ip add, for this do a nslook up and fill in the ip add instead of the the domain name. MSN  still fails , but its not v imp to me. Yahoo & google work fine 


I disabled ipv6 , now apt works fine... 

Digicam dint work well with gthumb... Installed gtkam and it works perfectly :)


Took a long time to fig it out, but at last have a stable USABLE ubuntu system.. :)

---

### Post by jvictor on 2005-10-28
Wanted to add this.. 
Use graveman for cd writing :eek:  , it works more or less fine .. no hassles till now

---

### Post by skskarda on 2005-10-31
I found another solution that was very easy.

[http://www.ubuntuforums.org/showthread.php?t=82402](http://www.ubuntuforums.org/showthread.php?t=82402)

Do expert install

-d1 when asked for cd installation parameters.

---

