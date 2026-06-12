---
title: "Well, I did it. Oneiric to Precise"
date: 2011-11-28
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by grahammechanical on 2011-11-28
Last night I used the code in post 5 of this thread

[http://ubuntuforums.org/showthread.php?t=1887567]("http://ubuntuforums.org/showthread.php?t=1887567")

+ an Update Manager update, to turn my testing Oneiric into a testing Precise and I am pleasantly surprised how stable everything is.

It looks like 11.10 but then it would, wouldn't it, at this stage of development. System Info tells me it is 11.10 Oneiric but System Monitor tells me it is 12.04 Precise and Software Sources tells me that I will be getting updates from the Precise repositories. So, it must be Precise Pangolin that I am now using.

This is what survived that change over:

1) My Unity plugin settings. The top panel is still transparent. The Launcher is hidden (my choices) and my chosen applications are still in the Launcher.

2) My app indicators are still there. The Keyboard layout icon still owrks.

3) Radio tray still works.

4) My one indispensable Windows program is still in the Launcher and it works.

5) XSensors is still in the Launcher and works.

What else?

I think it updated my Nvidia driver. I must check that.

Everything is as it should be and I am seriously thinking about making a very early switch over of my working 11.10 to a working 12.04.

Based on this experience I think that upgrading from 11.10 to 12.04 next spring will be less problematic than the upgrading from 11.04 to 11.10 that many have experienced.

If I had done a fresh install I might have had a different experience. I do not know. I also wonder if a 11.10 + Gnome shell conversion to a 12.04 + Gnome shell would be as trouble free.

Regards.

29/11/2011 Update: Yes, it did update the Nvidia driver from 280 to 285 - no issues. The only thing that has crashed is the zeitgeist-daemon due to 3 obsolete packages which I can easily fix. 

This system is so stable that I have decided that I will use it to do my work on - mainly word processing and listening to music as well as visiting these forums.

---

### Post by ventrical on 2011-11-28
Type in  at the terminal:

uname -a

 and it should give you somthing like this:

ventrical@ventrical-P4M266A-8237:~$ uname -a
Linux ventrical-P4M266A-8237 3.2.0-1-generic #3-Ubuntu SMP Tue Nov 22 11:17:48 UTC 2011 i686 i686 i386 GNU/Linux
ventrical@ventrical-P4M266A-8237:~$

3.2.0-1-generic being the name of the kernel I installed.

---

### Post by effenberg0x0 on 2011-11-28
lsb_release -a is also a good option:


$ lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu precise (development branch)
Release:    12.04
Codename:    precise

---

### Post by sammiev on 2011-11-28
I'm there. :) 

sam@sam-Satellite-L650:~$ lsb_release -a
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu precise (development branch)
Release:	12.04
Codename:	precise


A few broken packages but other wise OK.

QT 4 is given me a few errors in update manager.

---

### Post by sammiev on 2011-11-29
After todays updates all is well. :)

---

### Post by ventrical on 2011-11-29
Welcome aboard ! :)

---

