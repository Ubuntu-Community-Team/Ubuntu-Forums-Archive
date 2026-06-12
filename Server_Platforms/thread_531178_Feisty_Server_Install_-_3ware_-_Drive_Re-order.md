---
title: "Feisty Server Install - 3ware - Drive Re-order"
date: 2007-08-21
forum: Server Platforms
---

### Post by mizzouxc on 2007-08-21
I'm having some problems with disk re-ordering with a Feisty server install. As a little background I'm coming from SuSE, which orders my current hardware setup as this:

onboard SATA disk: sda  (boot disk)
3ware 9500 array:   sdb  (data storage)

When I go to install Feisty Server x64, it detects my 3ware raid card as sda and my  on board controller as sdb. I haven't changed a thing in my system configuration!

So I pull the 3ware card, forcing my on-board hard disk to become sda, install Feisty Server, boot it and all is happy. I shut down the system and install my raid adapter back in. The system boots fine because the device.map and menu.lst are properly configured. However, instead of the onboard sata disk being sda, it is now sdb. I'd like my onboard drive to be sda and the 3ware card array to become sdb. 

As another side point, fedora core 5 - 7 installers detect things as I wish, as well as knoppix, and slackware. 

Anyone have any suggestions on how to make Ubuntu detect onboard devices first and add-in adapters second, just like every other distribution on the market does?

---

### Post by mizzouxc on 2007-08-22
I worked again on this issue last night, couldn't find a resolution. Any ideas?

---

### Post by mizzouxc on 2007-09-12
Shameless bump, anyone have any ideas on a work-around. I know this is a common issue with debian, as they have posted it on their site as the #1 bug with their latest release.

---

### Post by smileypaul on 2007-11-30
Crap, I'll be doing this install in a week.. hopefully i dont have the same problems.. did you ever find an answer?

---

### Post by crouton on 2007-11-30
Check this thread: [http://ubuntuforums.org/showthread.php?t=468664](http://ubuntuforums.org/showthread.php?t=468664) and see if it helps.  I'll keep researching...

[edit] [http://ubuntuforums.org/showthread.php?t=599692](http://ubuntuforums.org/showthread.php?t=599692) has more info.  Neither thread appears to solve your particular issue, re: forcing a specific drive letter scheme.  But between these two links, playing with UUID and Label's should get you a bit closer to your goal.

---

### Post by mizzouxc on 2007-11-30
As far as I can tell, this is a Debian-based distribution only problem. I went to the Debian page awhile back and in their release notes, they mentioned this exact problem and it was a high priority fix. For the life of me, I cannot find this link now, but it was in the release notes. 

For now, it's still an annoyance. Especially when /dev/sda becomes sdb and you add a new drive that becomes sda and sda become sdb, etc. This makes attempting to format drives of identical size almost impossible! 

I have no problem mounting by UUID, etc. It's just darn annoying when you're trying to format drives and they're always changing on you. 

> **crouton said:**
> Check this thread: [http://ubuntuforums.org/showthread.php?t=468664](http://ubuntuforums.org/showthread.php?t=468664) and see if it helps.  I'll keep researching...

[edit] [http://ubuntuforums.org/showthread.php?t=599692](http://ubuntuforums.org/showthread.php?t=599692) has more info.  Neither thread appears to solve your particular issue, re: forcing a specific drive letter scheme.  But between these two links, playing with UUID and Label's should get you a bit closer to your goal.

---

### Post by crouton on 2007-11-30
Perhaps section 4.6.4 of [http://www.debian.org/releases/stable/i386/release-notes/ch-upgrading.en.html](http://www.debian.org/releases/stable/i386/release-notes/ch-upgrading.en.html) ?

It looks like you might be able to set driver load order using *initramfs-tools*.  I'd certainly want a test system setup rather than do it on a necessary box though. :)

---

### Post by mizzouxc on 2007-12-04
> **crouton said:**
> Perhaps section 4.6.4 of [http://www.debian.org/releases/stable/i386/release-notes/ch-upgrading.en.html](http://www.debian.org/releases/stable/i386/release-notes/ch-upgrading.en.html) ?

It looks like you might be able to set driver load order using *initramfs-tools*.  I'd certainly want a test system setup rather than do it on a necessary box though. :)

Luckily I found this problem on my test box before I deployed it on something serious. I love ubuntu on my laptop/desktop, but maybe it's just not ready for prime-time server for me. I'll have to give 7.10 a go with this, since I was using 7.04 when this problem first occurred--or move to a LTS distro. I'll report back if I get time to test these.

---

