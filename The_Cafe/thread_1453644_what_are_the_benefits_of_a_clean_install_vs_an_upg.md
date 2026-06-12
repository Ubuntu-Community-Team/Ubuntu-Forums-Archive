---
title: "what are the benefits of a clean install vs an upgrade?"
date: 2010-04-13
forum: The Cafe
---

### Post by mamamia88 on 2010-04-13
if you do a clean install with old home partition don't you have to reinstall drivers etc?  also wouldn't more settings be kept in tact with an upgrade?  i've been using ubuntu since 8.10 but have never actually upgraded before and always started over with each new release but this time i am pretty content with what i have and don't  want to lose anything

---

### Post by snowpine on 2010-04-13
Upgrades should work fine. If they don't, it is a bug in the Ubuntu upgrade manager. :)

More info here: [https://help.ubuntu.com/community/UpgradeNotes](https://help.ubuntu.com/community/UpgradeNotes)

---

### Post by mamamia88 on 2010-04-13
all right i will give it a try this time

---

### Post by WinterRain on 2010-04-13
I've noticed that upgrades are "iffy" at best. You will get the best results by clean installing. I don't even use the same home, as apps change and old configs can screw up the newer app. Considering upgrading can take hours with no guarantees of working well, I'll take a 1 hour clean install anyday.

---

### Post by forrestcupp on 2010-04-13
The benefits are that you get to see the changes they made to the installer, and you get to see how much better and easier things work out of the box.

That's about all.  Upgrades work very well, especially compared to what they were like a few years ago.

edit:  I guess with a clean install, it's easier to set up a different file system, like ext4.

---

### Post by FuturePilot on 2010-04-13
I always upgrade and I've never had a problem caused specifically by the upgrade. And I've upgrade many machines multiple times.

---

### Post by NightwishFan on 2010-04-13
The Ubuntu up-grader is quite clever. It has contingencies for some common stuff during upgrades.

---

### Post by ZarathustraDK on 2010-04-13
I always clean install, I want to see the installer and how default looks and feels like. :P

---

### Post by swoll1980 on 2010-04-13
There aren't any. I've upgraded every version of Ubuntu since 7.04 w/o a hitch. I can't see any reason why someone would want to do a reinstall over an upgrade. It just doesn't make sense to me.

---

### Post by toupeiro on 2010-04-13
I prefer upgrades as I hate having to reconfigure everything after fresh installs.  Upgrades preserve *almost* everything.  Evolution's upgrade didn't really work well this time around, so make sure you do a manual backup of your evolution settings prior to your upgrade (and by manual backup, I mean use evolution to create the backup).  ..unless you don't use it or have a lot of things to sync with it.

---

### Post by blur xc on 2010-04-13
> **swoll1980 said:**
> There aren't any. I've upgraded every version of Ubuntu since 7.04 w/o a hitch. I can't see any reason why someone would want to do a reinstall over an upgrade. It just doesn't make sense to me.

I'm going to upgrade this time around and I'm going the clean install route-  As I have been learning Linux, I've been screwing around with tons of junk, installed a lot of stuff I've long since forgotten about, and I'm looking forward to starting out w/ a clean slate this time around, only reinstalling what I really need.

BM

---

### Post by beetleman64 on 2010-04-13
I've always performed a clean install, although I performed an upgrade on my test machine and it worked perfectly. That said, since 10.04 is an LTS release I'll probably stick with my old methods.

---

### Post by swoll1980 on 2010-04-13
> **blur xc said:**
> I'm going to upgrade this time around and I'm going the clean install route-  As I have been learning Linux, I've been screwing around with tons of junk, installed a lot of stuff I've long since forgotten about, and I'm looking forward to starting out w/ a clean slate this time around, only reinstalling what I really need.

BM

Use computer janitor. People talk crap about it, but I think it's great. Make it easy to find, and delete those programs you forgot about.

---

### Post by sdlynx on 2010-04-13
I usually do a clean install, partly because I have already made a separate partition for /home and figure, why not.  I usually save like my fstab (of course some things are different due to formatting of the swap partition), so that I don't have to redo everything.  Even my settings are kept, and I feel that with a clean install I can get rid of apps that I never use, saving space (and bootup time).

Also, sometimes when I run upgrades it fails and stuff gets out of control.

---

### Post by madjr on 2010-04-13
with clean install to a new partition you can always **revert back**

also should be snapier and cleaner, the home and root dirs can have lots of crap over the years

better safe than sorry

also as a bonus you already have a live-cd in case you need it later

---

### Post by lovinglinux on 2010-04-13
> **WinterRain said:**
> I've noticed that upgrades are "iffy" at best. You will get the best results by clean installing. I don't even use the same home, as apps change and old configs can screw up the newer app. Considering upgrading can take hours with no guarantees of working well, I'll take a 1 hour clean install anyday.

+1

I always do clean installs. I have a separate home, but I have already experienced serious issues due to old configuration files. So whenever I do a new clean install I backup all my settings from home, then test if everything is working properly. If not, then I clean my home settings files and manually restore only those folders that I consider most important, like the ones that store encryption keys, passwords and stuff that cannot be re-configured by memory.

---

### Post by WinterRain on 2010-04-13
> **swoll1980 said:**
> It just doesn't make sense to me.

And to me, it doesn't make sense to upgrade. To each their own.

Looking around the forums, you will see a lot of "after upgrading, sound/video/wireless no longer works" threads. *And*, upgrades can take hours, while I can have everything back as it was in a little over an hour with a clean install. (only takes me 4 minutes to install from usb stick) So if only from a time standpoint, why would you upgrade and take a chance that something may break? It just doesn't make sense to me. ;)

---

### Post by swoll1980 on 2010-04-14
> **WinterRain said:**
> And to me, it doesn't make sense to upgrade. To each their own.

Looking around the forums, you will see a lot of "after upgrading, sound/video/wireless no longer works" threads. *And*, upgrades can take hours, while I can have everything back as it was in a little over an hour with a clean install. (only takes me 4 minutes to install from usb stick) So if only from a time standpoint, why would you upgrade and take a chance that something may break? It just doesn't make sense to me. ;)

I clone my hard drive in case I need to restore it. My updates never took that long, or I probably wouldn't upgrade either. It downloads the packages in about 30 minutes, then it spends 30 minutes installing.

---

### Post by jfreak_ on 2010-04-14
I have a rather customised system ie the UI is extremely different from the one you guys see regularly, the rgba patch has been implemented in a lot of programs, nautilus has been replaced by nautilus-elementary, many of the boot services have been removed etc etc. you think an upgrade will preserve all these tweaks? I shudder at the thought of doing all these things again.

---

### Post by handy on 2010-04-14
I usually upgrade everyday. Have done on this system for over two years & it is working at least as well as it ever has. :)

---

### Post by Khakilang on 2010-04-14
I have made clean install from 8.10 to 9.94 to 9.10 so maybe I will try the upgrade and see how it goes.

---

