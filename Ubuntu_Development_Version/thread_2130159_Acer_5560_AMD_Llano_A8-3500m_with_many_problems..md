---
title: "Acer 5560 AMD Llano A8-3500m with many problems."
date: 2013-03-28
forum: Ubuntu Development Version
---

### Post by vinibali on 2013-03-28
hi guys,
i made the big decide yday. i leave the w7 and will use the Ubuntu 13.04. im not so noob, so can do many things, but im already a beginner :)
i have an Acer laptop with a powerful A8-3500m@8GB of RAM(4*2) and 128GB Toshiba SSD with external 24" LCD
at the installer i killed the whole win7 partition(boot part remains), and made an ext4.
so 1st HUGE thing:

- **stucks at purple screen**, sometimes: about 5times it starts really quickly, and the other 5 times it stucks at splash screen. when it doesnt start the hdd led even not lights. i tried with just the laptop itself(without ext monitor and usb things) but still the same. when that cames, the comp freezes, just the longly pushed powerbutton help. almost everytime next time it starts perfectly.

- **stucks at shutdown**: almost the same, the small ubuntu logo cames and the red points are moving, but suddenly stops(or the whole screen turns into black) and just the old long pushed power button can help.

these was main things but have some more:

- **hot-swap HDD**(optibay) because of some reasons my optibay is works on, after the bios is alive. so i built in a small switch for the optibay and power on the hdd when i need it. in windows i can use that thing, the AHCI recognizes the drive, but here when i turn on the switch, nothing happens. and idea? 

- **Turionpowercontrol** for the quiet work. i set the power states(what i used on win already), after the processos dont throttles. it stays the lowest(p7) powerstate(400Mhz@0,65V) and everything is slow like ****

- **Have no wifi** (bcm43227), the installer told me at the installing(3rd party things), but i dont checked the box. now at the proprietary screen, theres just the AMD driver.

- In germany the youtube blocks many videos because of the **GEMA thing**. is there any hide ip program like in the windows? i want to use the chrome

Other things: Proprietary AMD driver, non-secure boot bios, further tired with the 12.10 there was the same problems.

thanks a lot, help me please! i can upload any log file, what u need ;)

---

### Post by mörgæs on 2013-03-28
Which release of Buntu are you using?

---

### Post by vinibali on 2013-03-28
13.04, but i tried the 12.10 futher, and there was the same issues

---

### Post by mörgæs on 2013-03-29
I would begin with solving the problems one by one. 

Regarding boot this thread might help you:
[http://ubuntuforums.org/showthread.php?t=1743535](http://ubuntuforums.org/showthread.php?t=1743535)

---

### Post by vinibali on 2013-04-02
however i deleted the ubuntu from my ssd, the usb live drive has the same issues, so tried with hat.
so the start/restart issue:
still start at the 2nd/3rd time, absolutely randomly. i tried with nomodeset/nosplash --verbose text switches, when it start i saw the commands etc, when not, the computer absolutely freezes itself. just the long pushed pwrbutton help for "restart"
i hope you have some other advices :D

---

### Post by mörgæs on 2013-04-02
No, sorry. You could maybe try to post in the thread I mentioned above.

---

### Post by vinibali on 2013-05-02
UPDATE:
im glad cos have reasonto to write here again.
so tday i tried the LMDE live usb thing. and finally i saw the kernel panic message. im pretty sure, if the problem is the same, however this LMDE has an older 3.2.0 kernel. but this edition of the Mint cant even start!!! i tried with the nomodeset/live/persistant/battery in/just laptop options, but i cant ever boot.
i hope it helps :) it was the most "rich" errorcode
[ATTACH=CONFIG]242093[/ATTACH]

---

### Post by vinibali on 2013-05-09
UPDATE:
looks like it works now. maybe some bugfix resolved my problem :)

UPDATEv2:
these was the 32bit installers. so the 64bit version still unuseable :(

---

