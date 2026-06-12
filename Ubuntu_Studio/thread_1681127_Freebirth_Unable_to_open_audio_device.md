---
title: "Freebirth: Unable to open audio device"
date: 2011-02-03
forum: Ubuntu Studio
---

### Post by the-penguin on 2011-02-03
Hey guys,

I recently downloaded freebirth but sadly it wont launch.
when launched from the command line it gives this output:
```
$ freebirth
Unable to open audio device.
```regards,
Jason

---

### Post by PiHalbe on 2011-02-10
I'm experiencing the same problem. Digging for a solution right now.

Also, the manual is not available: [http://www.bitmechanic.com/projects/freebirth/doc.html](http://www.bitmechanic.com/projects/freebirth/doc.html)

---

### Post by fvj on 2011-02-11
Hi folks,

@[the-penguin]("http://ubuntuforums.org/member.php?u=1005898"): I've noticed that also in the last Ubuntu Studio (10.10). 
The reason is that Ubuntu 10.10 dropped off the support of OSS (at the Kernel level)...

If you want to see why (and have time), just look here: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/579300](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/579300)

But, if you look in the source code of Freebirth, it's hardcoded to use /dev/dsp as a soundcard, and that's just no more here with 10.10!!!

Anyway, I find a solution here (in French): [http://yvesdelhaye.be/?dev-dsp-via-asound-sous-ubuntu-10](http://yvesdelhaye.be/?dev-dsp-via-asound-sous-ubuntu-10)

It is based on that topic (in English): [http://art.ubuntuforums.org/showthread.php?t=1607546&page=2](http://art.ubuntuforums.org/showthread.php?t=1607546&page=2) 

The solution is to do the following: install alsa-oss, then create a file /etc/asound.conf as indicated ("hw:0,0" is OK if you just have one soundcard, or you want to use "hw:1,0" if you have two and want to use the second one) and, finally, start Freebirth with ```
/usr/bin/aoss /usr/bin/freebirth
``` it works by me (the interface is strange and ugly and not refresh so good, but that's another story, the sound is OK...).

If you were recording video (+sound) with mencoder, that link (again in French, but look at the code in the last post) give a solution: [http://forum.ubuntu-fr.org/viewtopic.php?id=416751](http://forum.ubuntu-fr.org/viewtopic.php?id=416751)

Bonne chance (=Good luck)

@PiHalbe: the Freebirth project is now hosted here (and seems somehow almost dead): [http://sourceforge.net/projects/freebirth/](http://sourceforge.net/projects/freebirth/) 

You can find a (minimal) documentation here: [http://freebirth.sourceforge.net/doc.html](http://freebirth.sourceforge.net/doc.html)

Have fun,
FvJ

---

### Post by PiHalbe on 2011-02-15
Ok, thanks for the update. I found the SF project, but it also seemed dead to me.

If I find the time for it, I'll try the OSS emulation. The package should be removed if it cannot be run without emulation on a generic Ubuntu setup.

Also, I could not find any alternatives to this package on Ubuntu. There's apps for Windows, iOS and Android, though.

---

### Post by imbjr on 2011-11-26
This application seems pretty b0rked under Xubuntu at least:

imbjr@pc:~$ aoss freebirth
Calculating coefficient table.................................................................................................................................................................................................................................................
Done
Segmentation fault

---

