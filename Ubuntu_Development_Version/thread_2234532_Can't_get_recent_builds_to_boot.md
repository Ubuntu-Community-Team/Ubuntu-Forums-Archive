---
title: "Can't get recent builds to boot"
date: 2014-07-15
forum: Ubuntu Development Version
---

### Post by sgage on 2014-07-15
Hello All, long time no post...

Anyway, I thought I would try out the latest UG, and burned it to my trusty USB stick with unetbootin, as I have done for years. When I try to boot from it, I get a "No Operating System" error msg. Everything looks in order on the USB stick, as far as I can tell.

Is there some new trick to making a bootable USB stick in Utopic? Do I need to use a particular tool? Is this a known issue?

TIA...

---

### Post by grahammechanical on 2014-07-15
I have just run the live session of today's daily Ubuntu Gnome image without any problems. Used a DVD. Sorry, I am not getting this problem.

Regards.

---

### Post by ibjsb4 on 2014-07-15
What works for me ..

Download the mini or remix iso to the unetbootin installer and build it.
```
sudo apt-get install ubuntu-desktop
```

---

### Post by sgage on 2014-07-15
Thanks for your feedback, guys.

I have managed to make a bootable USB stick. I used gparted to install a new partition table, and let it format the stick. Things worked nominally after that. That is, until it got to the phase where it tries to format the partition for /.  It stuck there forever ("creating ext4 partition on /dev/sda2"). 

When I have more time to play, I'll try running the installer from the live desktop, vs. booting right to it. Believe it or not, I've found that to make a difference in the past. 

I could also go the mini iso route. Or maybe just wait a week or two :KS

---

### Post by crcarson on 2014-07-17
Think I saw this also.  Hitting tab will present some boot options "live" to boot to the Utopic system, "live-install" to boot to the install start, and others.

---

### Post by fooman on 2014-07-18
thanks crcarson....i had problems even getting the usb startup disc creator to work,  so i installed unetbootin and used that instead.

when i booted with the flash drive,  i got the "no operating system found" error as well.....but pressing the "tab" key brought up a list of options: ubnentry0 - ubnentry8

choosing the first option (ubnentry0) got me nowhere...the second option (ubnentry1) brought up the "live" environment and worked fine.  the third option (ubnentry2) brought up the install menu,  and that seems to work fine as well.

did not try the other options.

---

