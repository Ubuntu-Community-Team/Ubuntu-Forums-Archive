---
title: "kernel-kbuild-3.6??"
date: 2005-08-01
forum: Repositories &amp; Backports
---

### Post by joshpelkey on 2005-08-01
Running Hoary and need kernel-kbuild-3.6:

I'm trying to get my winmodem to work, and I'm having a hard time getting a hold of kernel-kbuild-3.6.  I have no connection to the internet, except at my work.  I tried to download a file from [http://packages.debian.org/stable/devel/kernel-kbuild-2.6-3](http://packages.debian.org/stable/devel/kernel-kbuild-2.6-3), but I couldn't get it to work on my computer.  I may have done something wrong there though.  Any clue where I can get kernel-kbuild-3.6?  I tried [http://packages.ubuntu.com/](http://packages.ubuntu.com/) and found it, but when I tried to dl it, it couldn't find the file.  Any help would be much appreciated.

Josh

---

### Post by joshpelkey on 2005-08-03
[COLOR=Red]**Disregard my post inquiring the location of kernel-kbuild-3.6**[/COLOR].  For anyone who may care how I resolved my issue and got my SmartLink modem working, read on:

After using [scanmodem](http://linmodems.technion.ac.il/packages/scanModem.gz)  to figure out my Linmodem chipset and recommended drivers, the output told me I may need kernel-kbuild-3.6 installed in order for everthing to work correctly.  That turned out to not be the case.  "scanmodem" recommended I try out [slmodem-2.9.9d]( http://linmodems.technion.ac.il/packages/smartlink/).  After downloading and installing, modprobe slamr wasn't working correctly.  I was dissapointed, because I had gotten my modem to work on an earlier kernel version.  I finally did a "dmesg | grep slamr" and saw an output of something like this:

slamr: module license 'Smart Link Ltd.' taints kernel.
slamr: SmartLink AMRMO modem.
slamr: device 10b9:5457 is grabbed by driver serial 

I wasn't sure what that meant, but after reading for a while [a long while] I found the solution.  Eventually I downloaded and installed [ungrab-winmodem](http://linmodems.technion.ac.il/packages/smartlink/ungrab-winmodem.tar.gz).  
I needed to issue modprobe ungrab-winmodem before I did a modprobe slamr, and finally I could "slmodemd slamr."  I was pumped when I saw that it worked.  That wasn't the greatest of explainations, so if you are having a similar problem and need more guidance, feel free to email me, [email]yojdork@gmail.com[/email], if you'd like.  Later!  And thanks to anyone who looked for kernel-kbuild-3.6 for me!

Josh

---

