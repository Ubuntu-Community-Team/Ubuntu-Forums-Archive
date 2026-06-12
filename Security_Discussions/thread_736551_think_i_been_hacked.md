---
title: "think i been hacked"
date: 2008-03-26
forum: Security Discussions
---

### Post by oxtail75 on 2008-03-26
i think i may have been hacked

i am haveing a number of odd problems!!!

cpu running between 60 and 80% all the time
locked out of my home folder in sum cases file manager will not open at all
nearly all my ram is being used up
slow internet conntection tuck nearly an hour to get to this site

do i need to reinstall or can sum one help me fix this

---

### Post by SunnyRabbiera on 2008-03-26
well what have you done exactly, I dont think you have been hacked but its possible you might have misstepped somewhere.

---

### Post by oxtail75 on 2008-03-26
nothing as far as i know i installed barsero 2day thats it really

---

### Post by ryanhaigh on 2008-03-26
Using the terminal use the command top to see what is using all your cpu. You can also install iftop to check where all your bandwidth is going. The command w (yes just one letter) should tell you who is logged onto your system.

---

### Post by wieman01 on 2008-03-27
If it really turns out you have been hacked, the only option you have is reinstalling your system entirely. Back up all your data and fire up the Live CD.

---

### Post by hyper_ch on 2008-03-27
instead of using "top" I'd rather use "htop"

```

sudo apt-get install htop

```

and then run it by

```

htop

```

---

### Post by oxtail75 on 2008-03-27
i went to use it this moring and it had froze on me so i rebooted and i get nothing just a blank screen i didnet even get a boot screen

---

### Post by Dr Small on 2008-03-27
No GRUB either?

---

### Post by wieman01 on 2008-03-27
It sounds more like a hardware issue to me. I could be wrong, but it's odd...

---

### Post by oxtail75 on 2008-03-27
i don't know if grub is installed as i do not dual boot

---

### Post by Kevbert on 2008-03-27
Sounds like a memory chip problem.  If you have a live CD, it may be worth performing a memory check.

---

### Post by oxtail75 on 2008-03-27
thanx how do i do that

---

### Post by Kevbert on 2008-03-27
If you have a Ubuntu CD, all you need to do is boot from the CD and it's a menu option.  
You may need to go into the bios to set your CD to be the first item to boot from.  When you first turn on the PC you'll need to press a key (normally F2 or Del) as the PC is starting.  In bios there will be a menu item, something like Advanced BIOS Features where I think the boot devices are.  You want to set the first boot device to be CD, second to Hard disk.  Do Not Change anything else!!!  Now Save the changes (probably F10).  Put the CD in the drive.  The PC should now look for a CD prior to looking at the  hard disk for a boot file when you boot-up.

---

### Post by oxtail75 on 2008-03-27
running a live cd now and it all seems to be working

---

