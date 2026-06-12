---
title: "Lubuntu installs then locks up"
date: 2016-05-16
forum: Ubuntu/Debian BASED
---

### Post by DPMR on 2016-05-16
Gets to a blank screen then screen locks with this line.
/dev/sda1: clean, 122767/3538944 files, 954029/14131968 blocks

---

### Post by kc1di on 2016-05-16
we need a bit more information to be of much help.
What machine , Ram, Graphics card Etc would be a start. 
Which version of lxle ?

---

### Post by DPMR on 2016-05-16
Toshiba NB305 - 2gig ram - 1.66 atom - 60 gig ssd - Lubuntu 16.04

I found the problem. It was a failure connected to the USB stick.

I used ctrl-alt-del to reset computer and noticed a screen flashed showing something about inserting disk,
I then realized the locked screen was the installer waiting for the next disk.

I had Lubuntu 15.10 on disk so I tried using that instead of USB stick. It worked fine. NB305 is up and running on that.

I do wonder now what caused the error Pendrive's Universal Linux UFD Creator or the distro itself. The USB stick
booted up fine and ran 16.04 from the stick, so it was just a failure when I tried to install it. 
I have used the converter program many times before, so it makes me think it was the way the distro was compiled.

Suppose I should file a bug report.

---

