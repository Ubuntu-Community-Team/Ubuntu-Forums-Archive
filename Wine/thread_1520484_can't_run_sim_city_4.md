---
title: "can't run sim city 4"
date: 2010-06-29
forum: Wine
---

### Post by soluckytouselinux on 2010-06-29
hi everyone. have a problem trying to install sim city 4. i keep getting weird error message. here's a snapshot of the problem. i'm probable just missing a simple step somewhere. thanks everyone. cheers! :confused:

---

### Post by Frogs Hair on 2010-06-29
> **soluckytouselinux said:**
> hi everyone. have a problem trying to install sim city 4. i keep getting weird error message. here's a snapshot of the problem. i'm probable just missing a simple step somewhere. thanks everyone. cheers! :confused:

I went to site and found that Sim City 4 is a Microsoft app I started to download the demo an it stated it was an MS Dos application. you could read up on and install Wine from repository . Wine allows you to run some MS software.

---

### Post by Kimm on 2010-06-29
Right-click the file and select preferences, then go to "Permission" and check "Allow executing file as program"

After that it should work, assuming that Wine can run this game properly (and that you have wine installed)

---

### Post by soluckytouselinux on 2010-07-01
i tried to right click to change permission but it won't let me change anything. i have wine installed from the repos. i don't understand it. been using wine for a long time, this one is a first for me. thanks for all the help

---

### Post by steveneddy on 2010-07-01
> **soluckytouselinux said:**
> hi everyone. have a problem trying to install sim city 4. i keep getting weird error message. here's a snapshot of the problem. i'm probable just missing a simple step somewhere. thanks everyone. cheers! :confused:

All that transparency makes that hard to read. 

Turn off compiz and take the snapshot again.

You know that is if you use gausian blur you won't have such an issue reading the window doe to windows behind - right?

EDIT:

Or start using Ksnapshot to take a screenshot.

---

### Post by llamabr on 2010-07-01
wine is very rarely the correct solution.  If you really need to run windows programs, probably you should be running windows.

I don't know if sims runs natively in ubuntu.  probably not.  it's very unlikely that it's going to run correctly in wine.

---

### Post by Kimm on 2010-07-02
> **soluckytouselinux said:**
> i tried to right click to change permission but it won't let me change anything. i have wine installed from the repos. i don't understand it. been using wine for a long time, this one is a first for me. thanks for all the help

Ah right, sorry I missed that the file was on a CD. You could try copying the entire contents of the disk to a folder on your hard-drive, then change the permissions and try to run the installer from there. There is no guarantee that this will work, its possible the installer will refuse to run if not on a disk.

> wine is very rarely the correct solution. If you really need to run windows programs, probably you should be running windows.

I don't know if sims runs natively in ubuntu. probably not. it's very unlikely that it's going to run correctly in wine.


Wine works fairly well for a lot of things. A quick google search for "Sim City 4 Wine" [yields positive results]("http://tombuntu.com/index.php/2007/04/06/simcity-4-on-ubuntu-with-wine/"). The game is not very new, and from experience older applications are more likely to work than new.

---

### Post by Jakiejake on 2010-07-02
> **Kimm said:**
> Ah right, sorry I missed that the file was on a CD. You could try copying the entire contents of the disk to a folder on your hard-drive, then change the permissions and try to run the installer from there. There is no guarantee that this will work, its possible the installer will refuse to run if not on a disk.



Wine works fairly well for a lot of things. A quick google search for "Sim City 4 Wine" [yields positive results]("http://tombuntu.com/index.php/2007/04/06/simcity-4-on-ubuntu-with-wine/"). The game is not very new, and from experience older applications are more likely to work than new.

I had to do this morning!
It works if you do that!

---

### Post by philinux on 2010-07-02
Moved to Wine forum.

---

### Post by migs73 on 2010-07-02
If you want to take a snapshot just press your Print Screen Button on your keyboard (for your entire desktop) or Alt+PrintScreen for just the active window. No need for fancy programs!!

Ubuntu then asks what you want to do with the screenshot.;)

---

### Post by soluckytouselinux on 2010-07-03
hi everybody. i have fixed my problem. i put the disk in my dvdrw and went to wine to browse cd. found it on my machine, and just clicked on autorun. when it came to putting in disk 2, i had to unmount the first cd and went back into wine to install. thank-you for all your help. i hope this helps others.

---

### Post by Trippmeister on 2010-08-20
I suppose I'm a bit late on this, as you seem to have solved the problem, but in case anyone else is looking for info on running SC4 in Linux I'd suggest the following links:

Installation instructions & troubleshooting:
[http://www.simtropolis.com/omnibus/index.cfm/Main.SimCity_4.Running_Sim_City_4_on_Linux]("http://www.simtropolis.com/omnibus/index.cfm/Main.SimCity_4.Running_Sim_City_4_on_Linux")

Discussion thread:
[http://www.simtropolis.com/forum/messageview.cfm?catid=22&threadid=96881]("http://www.simtropolis.com/forum/messageview.cfm?catid=22&threadid=96881")
(You'll have to register at Simtropolis if you want to post on this thread)

Good luck!

---

