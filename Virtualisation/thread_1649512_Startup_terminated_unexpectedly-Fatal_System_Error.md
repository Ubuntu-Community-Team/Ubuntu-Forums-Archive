---
title: "Startup terminated unexpectedly-Fatal System Error!"
date: 2010-12-20
forum: Virtualisation
---

### Post by surati on 2010-12-20
Hallo 
 I&#7743; a new user to ubuntu and am struggling a few days long with the installation of windows7 on virtualbox(Puel).  I installed virtualbox following the instructions described on it&#347; website ([http://www.virtualbox.org/wiki/Linux_Downloads](http://www.virtualbox.org/wiki/Linux_Downloads)). Everything seemed to function... but everytime I start windows7, after 35 min. the startup process is unexpected determinated with this message:

[COLOR=Black][B]Stop: c000021a  Fatal System Error
The initial session process or system process terminated unexpectedly with a status of 
0x00000000 (oxc0000017 0x001003a8 ).
The system has been shut down.[/B][/COLOR]

Doe&#347; anybody have an Idea why?
:confused:
Surati

---

### Post by theasprint on 2010-12-20
Hi,

From what I've checked, it seems to be a BSOD (Blue Screen of Death)
A BSOD is like a crash for Windows.

Here's what I've checked
> that certain BSOD is a kernel-side failsafe. it'll happen when CSRSS exits or is killed. (see: process explorer, csrss.exe > end process)
So possibly your csrss.exe got terminated.

Hope this helps.

---

### Post by surati on 2010-12-20
Thanks for the fast answer:). I will now google around to find out what csrss is...
The funny thing is that once, befor I got this message the startup of windows7 continued longer and the installations process was even getting started (I had to stop it because of lack of memory on the partition).

---

### Post by surati on 2010-12-27
Hi 
I run out of ideas for a possible solution, I just cann´t sartup windows7. 
I installed the new version of VB (4.0.0), updated everything and got then a new (different)Error message.
 Maybe its just a simple problem which a newbie like me easyly overlook? maybe any file-conflict through my install-uninstall experiments?A missing driver? Boot/grub-problem? Doe&#347; anybody have an idea???

---

### Post by surati on 2010-12-27
Hi
 I run out of ideas for a possible solution, I just cann´t sartup windows7.
 I installed the new version of VB (4.0.0), updated everything and got then a new (different)Error message.
 Maybe its just a simple problem which a newbie like me easyly overlook? maybe any file-conflict through my install-uninstall experiments?A missing driver? Boot/grub-problem?
 Doe&#347; anybody have an idea???

Oops, sorry, I posted it twice, don´t know how to delete this one.

---

