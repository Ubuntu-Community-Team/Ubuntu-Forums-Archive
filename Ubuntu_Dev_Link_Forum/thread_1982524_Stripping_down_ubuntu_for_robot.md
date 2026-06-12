---
title: "Stripping down ubuntu for robot"
date: 2012-05-18
forum: Ubuntu Dev Link Forum
---

### Post by sebflippers on 2012-05-18
Hi all,

I have embedded linux running on a pandaboard (google it).  I use it for camera- based tracking.  It then sends processed information to the robot controller.

Right now, the controller boots in about 20 seconds, and is immediately ready to start working.  My pandaboard requires me to log in and then open up the main tracking program.  It also boots a bit slower than the controller.

What I want to do:
-Get rid of the X server (no monitor will be plugged in anyways)
-get rid of unity
-have it go right to the terminal if I happen to plug a monitor in
-log in automatically
-launch my tracking program and launch cloud9 ide on startup

by getting rid of graphics things, I hope to drastically increase boot time (its @ about 25 seconds right now).

I can set auto-login and get those programs to start by themselves, but I am unsure about what effect the absence of X.org and unity will have.  Also, can I get rid of the login manager altogether?

Thanks for the help
Sebflippers

---

### Post by MadCow108 on 2012-05-19
there is a minimal install cd:
[https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)

I never used it in ubuntu, but its probably similar to the debian net installer where you can select which packages you want

---

### Post by roelforg on 2012-05-19
> **MadCow108 said:**
> there is a minimal install cd:
[https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)

I never used it in ubuntu, but its probably similar to the debian net installer where you can select which packages you want

Using debootstrap and --variant=minbase is easier as i think there's no cddrive on the bot.

---

### Post by sebflippers on 2012-05-20
> **roelforg said:**
> Using debootstrap and --variant=minbase is easier as i think there's no cddrive on the bot.

The plan is to use sd cards to boot, and we can swap them to change the robot's functionality.

---

### Post by sebflippers on 2012-05-20
wait a second.  I forgot to mention that it uses omap architecture.  This means that I can't use standard ubuntu anyways.  I currently use a .img file I found online which has a modified omap ubuntu.  I think the best way would really be to start like that and then take stuff off one by one.

---

### Post by Bachstelze on 2012-05-21
I suggest that you use an OS with official ARM support instead of Ubuntu. If you don't want to go too far, you can use Debian.

---

