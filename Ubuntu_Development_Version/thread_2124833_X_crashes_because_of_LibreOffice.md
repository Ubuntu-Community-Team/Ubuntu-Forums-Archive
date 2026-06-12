---
title: "X crashes because of LibreOffice"
date: 2013-03-12
forum: Ubuntu Development Version
---

### Post by wribeiro on 2013-03-12
Frequently, when opening LibreOffice Writer via Unity panel, or after that, when opening a doc or odt file, a general crash happens in user interface, the screen goes black or flashes, the whole system crashes. sometimes lightdm restarts and returns to the login screen.
I would like to report this bug, but do not know which log file should I attach to allow debugging.

Ubuntu 13.04 32bits
LibreOffice 4.0.1.2

HP Pavilion dv6000
NVidia Graphics - GeForce 7150M / nForce 630M
nvidia-304-updates driver

---

### Post by dino99 on 2013-03-12
you should find a crash file inside /var/crash/ , simply right click on it to report with Apport; all the needed task is done by apport to post a bug on launchpad.
maybe you can grab some more info into .xsession-errors too.

---

### Post by wribeiro on 2013-03-12
Dino99, thank you for the reply!
The problem is that files inside /var/crash/ are not being updated when this bug happens. Files have modify date of yesterday, although today the bug have happened at least 3 times.

---

### Post by grahammechanical on 2013-03-12
There was an update to Libreoffice yesterday and another one today. What is the build ID? On my system I have Libreoffice 4.0.1.2 Build ID:400m0 (Build:2) You get this info from the Libreoffice help menu.

What I find strange about this issue is that is does not trigger a crash report. On development releases the crash reporter utility Apport is enable by default. When a system crash is detected Apport should tell you that there has been a crash and invite you to report it. If you search for Apport in the Ubuntu Software Centre you will see if it is installed or been removed. You can do the same using Synaptic Package Manager but you will have to install Synaptic first.

Just a thought. I might not be the Xserver that is crashing. It could be Compiz the compositing/window manager. What to do? Not sure at all. Try another video driver?

Regards.

---

### Post by wribeiro on 2013-03-12
Libreoffice 4.0.1.2 (Build ID: 400m0(Build:2))
Apport is installed here, version 2.9.1-0ubuntu1.
The crash occurred once more time and there is no trace. 

I guess the crash is related to this bug: [https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers/+bug/568492](https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers/+bug/568492)
The cause seems to be the nvidia driver, which was recently upgraded to nvidia-304-updates (304.84-0ubuntu2), without improving.
Nouveau driver does not work on HP Pavilion dv6000 - GeForce 7150M / nForce 630M/integrated/SSE2/3DNOW! (is an adventure installing the operating system under heavy flicker, unable to see the commands in screen, but it's only possible on that way)

I had so many problems with video driver that I chose to abandon Ubuntu 12.10 and use Ubuntu 13.04 alpha. Unfortunately there was no significant improvement.
When connecting an external monitor the issue became more frequent and it is impossible to use LibreOffice.

---

### Post by alphacrucis2 on 2013-03-12
> **wribeiro said:**
> Libreoffice 4.0.1.2 (Build ID: 400m0(Build:2))
Apport is installed here, version 2.9.1-0ubuntu1.
The crash occurred once more time and there is no trace. 

I guess the crash is related to this bug: [https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers/+bug/568492](https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers/+bug/568492)
The cause seems to be the nvidia driver, which was recently upgraded to nvidia-304-updates (304.84-0ubuntu2), without improving.
Nouveau driver does not work on HP Pavilion dv6000 - GeForce 7150M / nForce 630M/integrated/SSE2/3DNOW! (is an adventure installing the operating system under heavy flicker, unable to see the commands in screen, but it's only possible on that way)

I had so many problems with video driver that I chose to abandon Ubuntu 12.10 and use Ubuntu 13.04 alpha. Unfortunately there was no significant improvement.
When connecting an external monitor the issue became more frequent and it is impossible to use LibreOffice.


You could try one of the other nvidia drivers. At least on my setup I get offered a choice of several different proprietary nvidia drivers. As to which one is considered the "normal" one to use I have no idea.

---

### Post by wribeiro on 2013-03-13
I tried all available drivers. 

- Nouveau, the default driver, results in a heavy flicker, screen is unreadable.
- nvidia-173 is the worst of all. The message is as follows: "The screen is running in low-graphics mode. Your screen graphics card, and input device settings could not be detected correctly. You will need to configure this yourserf."
- nvida-310, nvidia-313 sets wrong resolution, do not use acceleration, compiz do not work, Unity panel/bar disappear.
- 304-experimental also dont work.

The only one that works is nvidia-304-updates, but LibreOffice is unusable: [https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers/+bug/568492](https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers/+bug/568492)

The question is: Why only LibreOffice??

---

### Post by wribeiro on 2013-03-14
I really hope that Canonical does not release version 13.04 without solution for this, since there is no way to get around, except stop using LibreOffice and create a virtual machine with Windows. The worst possible!

For now, would be sufficient to report the problem in Launchpad. The biggest help of this forum I need now is to locate a log file on my computer that allows the tracking error.

---

### Post by pqwoerituytrueiwoq on 2013-03-14
i am using the 313.26 nvidia driver on my desktop on xubuntu 13.04 and i was able to open libreoffice writer with no issues

---

### Post by wribeiro on 2013-03-15
I'll try xubuntu.
Thanks for suggestion.

---

### Post by gianluca3 on 2014-01-29
hello, 

i have the same problem and no file filled in /var/crashes

the only way to exit from this is to ctrl+alt+f1 and then killall Xorg. when i restore Xorg libreoffice always works (?!)

i'm using ubuntu 12.04 with 
LibreOffice 3.5.7.2 
Build ID: 350m1(Build:2)

if someone know how i could reproduce a bug report i would appreciate.
best
g.

---

### Post by Elfy on 2014-01-29
Closed.

You've tagged onto the end of a development thread. 

Start a thread of your own in General Help [http://ubuntuforums.org/forumdisplay.php?f=331](http://ubuntuforums.org/forumdisplay.php?f=331)

---

