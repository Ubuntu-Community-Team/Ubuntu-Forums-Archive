---
title: "Kubuntu - upgrade and install experience"
date: 2019-01-07
forum: Ubuntu, Linux and OS Chat
---

### Post by mastablasta on 2019-01-07
Happy new year everyone.


I wanted to write about my upgrade/install experience. We had a bit longer holidays over here, and with some "special" offers for the needed equipment i decided it was time to move to linux (apart from some old games).


1.


First i had to do a dualboot with Windows XP leaving all data there intact. Target was the old single core AMD 3200+ PC with 4 GB DDR2 RAM and nvidia GT730 2GB GPU card. I couldn't do a simple dualboot since i didn't have enough space at the start of the windows drive. Apparently you need it more for the GRUB nowadays. I didn't want to move partitions since it is a bit dangerous. After testing the OS, i got a new hard disk and installed linux there. Roughly 30 minutes later i was up and running with Kubuntu 18.04. All hardware stuff recognised, i installed the recommended nvidia driver and started to add the needed apps. So far performance is good (a lot faster than WinXP and very responsive) and i hope it can stay there. i created a small grub-reboot script & desktop launcher to make it easy for kids to reboot to windows once, for some games. After they are finished there, all they need to do is turn off or reboot the PC and we are back in linux. I haven't started with widnows games installs in wine and i plan to add steam. But overall this is the experience once should have with (desktop) linux.


*Things i wish i did: I maybe should have gone with BTRFS, but i was kind of in hurry and EXT4 layout was more familiar. Also perhaps i should go with separate home.*


2. 
Second was double upgrade from Kubuntu 14.04 LTS 32 bit -> Kubuntu 16.04 32bit -> Kubutnu 18.04 32bit (which is the last 32bit). I initially wanted to upgrade to 16.04 only, but Kubuntu 16.04 is also suported only until april 2019. This did not go as planned. OS started the upgrade (after backup) and said it can not perform it and that it will revert to previous state. First of all i was missing a reason for not performing upgrade (this was afterall a relatively stock 14.04 with printer drivers being the only proprietary drivers on it). Secondly, it didn't reverse to previous state.


I then forced the upgrade to complete. it said there are not upgrades available, so i just ran apt-get update and upgrade commands. everything was downloaded and old OS was overwritten with defaults form new OS. on reboot it gave kernel panic. while the kernel was panicking i wasn't. i had the 18.04 install DVD, so i thought why not just install over the bad install and be done with it. so it went warning me it will delete the files blah blah blah... i just let it plough through. then came the final part of install where things went weird. it said attempting to install previous applications. huh? why? it said it would delete the folders. anyway after it appeared to have some success it couldn't install one app and the next part was strange. instead of doing a reboot the installer said it will now stop the install and boot into live session so i can troubleshoot and then reinstall it again. whoa?! i mean why not just delete the offending app and be done with it?


anyway about 6 hours after i started with upgrade i nuked the partition and went fresh. turns out it also had too little space for new (?) GRUB. this is interesting as only when i decided for new OS the manual partitioning warned me of this, but not the upgrader or installer where i performed the overwriting install. 


Final result - another awesome version of Kubuntu (this time 64bit). looks like sound is working now. having some issues with dosbox (exiting from fullscreen to plasma messes it's resolution up). but overall as work PC it works nicely and performs well. i can't do much gaming here, because GPU is old, but mostly because i think it overheats (or at least it used to - i got some new fancy fans installed).


*Things i wish worked better: the upgrade process. process is seriously flawed and this is on a relatively stock version. i can't imagine what would happen if i had my own theme, icons, GPU drivers...*


3 and 4 still to come :-) i have 2 more upgrades a dualboot win7 starter and 14.04 64bit with AMD FLGRX drivers and printer drivers. this one really worries me. especially with these new start of disk requirements. not sure what i will do there. i will post in help section after i have the chance to investigate. the 4th one will be server upgrade form 14.04 to 16.04. and probably i will just go all the way to 18.04. but server is faster & much less complicated and i might just do a fresh 18.04.


Another issue i had is that almost no USB creator can create a good linux live USB. after investigating the issue it seems they do not work properly with isolinux or something. so eventhough their version is from Oct 2018, they can't load live linux OS on USB. well they load it but it it unbootable. ridiculous. the only one that can do it is apparently rufus, which doesn't work on XP. the DVD works well as image is the same as on website. just in case anyone was wondering why i used DVD as install media.

---

### Post by Erik1984 on 2019-01-08
Congrats with the upgrades :D How do you like the 'new' KDE? I have a 18.10 for a couple of weeks now and it has been a pleasure to use. Have used KDE 4 (up till Trusty) for years and enjoyed that too, but the new KDE has much better defaults.

---

### Post by mastablasta on 2019-01-09
Yes, the new KDE5 has some better defaults. Some icons (in settings) are a bit strange - they could choose something more representative. But there is still text next to it.

It is more responsive than 4 when desktop effects are on. so far the biggest issue i ran into was going from full screen dosbox back into KDE - it messes up the resolution. I bet there is only some default setting that is wrong. the defaults are otherwise quite sane and make much more sense.

I also haven't had the time to try out wine. hopefully it works well.

---

### Post by SeijiSensei on 2019-01-09
I never upgrade versions.  I maintain a separate home partition and have a couple of partitions devoted to operating systems.  I'll install a new Kubuntu version into one of those spare partitions, point /boot and /home at the appropriate locations, and start it up.  If things work well I can stick with the new version.  If things get dicey, I can revert to the older version.

Right now I'm running the 19.04 beta which looks nice and seems quite stable.  Usually I stick with LTS versions, but I decided to give 19.04 a try.

---

### Post by mastablasta on 2019-01-10
looks to me like home would not be enough in this case. and i would also need a separate /boot folder. the system should not invite user to upgrade when there were such major changes made that the upgrade could actually not be possible. at least not in easy way. the grub needed OS partition to be moved or reduced.

---

### Post by acheronuk on 2019-01-10
Regards 14.04 -> 16.04 upgrade, releasee notes are quite clear on this.

[https://wiki.ubuntu.com/XenialXerus/ReleaseNotes/Kubuntu](https://wiki.ubuntu.com/XenialXerus/ReleaseNotes/Kubuntu)

> **14.04 LTS to 16.04 LTS upgrade**

 **WARNING**:  LTS to LTS upgrade to Xerus is currently problematic and should not be  attempted. Please install a fresh copy of 16.04 instead. To prevent  messages about upgrading, change Prompt=lts to Prompt=normal or  Prompt=never in the /etc/update-manager/release-upgrades file.

---

### Post by mastablasta on 2019-01-11
the message should be pushed to muon in some way, to disable it's prompts. i didn't see that note, never occurred to me that upgrade from LTS to LTS would be left on "problematic" for so long. to me personally it doesn't matter so much, i just wish i saw that release note sooner i would nuke it immediately :) and save quite a bit of time. i followed the procedure of backing up the data and i know how to restore it. someone that is less experienced might have more issues.

this also means i need to star a plan for a fresh install of 18.04 on the laptop. data won't be an issue there (not much of it and easy to reinstall). the only issue that i could still face is the GRUB needing more space at the start of disc (windows7 is there). i need to investigate that as well as AMD drivers. the 14.04 FOSS drivers were quite bad compared to fglrx - in acceleration and power management.

---

