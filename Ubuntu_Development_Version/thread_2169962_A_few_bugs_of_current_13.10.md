---
title: "A few bugs of current 13.10"
date: 2013-08-24
forum: Ubuntu Development Version
---

### Post by startas on 2013-08-24
So, first bug is very big and buggy global menu bar in installation, it takes half of my screen, so you have to "try ubuntu", and then you can run install from there, otherwise you just cant see any buttons because of gigantic global menu bar, plus vsync is missing from installation too - these bugs are a 3-4 weeks old.
P.S. intel hd graphics.

Another bug appeared from day 22 and newer daily isos - when you boot into live mode to install ubuntu and press the install icon in dash, nothing happens - no error, no setup window.

Dont know how to reports bugs otherwise,  because ubuntus integrated bug reporting system never ever works, just crashes since 80's :)

---

### Post by grahammechanical on 2013-08-24
Are these Saucy Salamander bugs? Or are they ISO image bugs?

For months during the Rairing Ringtail development cycle I could not run a live session without using a F6 option. I also found that the installer would crash while copying files claiming there was not enough disk space but if I started the installation from the live session desktop the install would not crash.

I am not surprised anymore that there are issues with daily ISO images of development versions. 

I also have seen that mulitple top panel lines bug. It was there in the image of the 16th August and it is still there in the image of 22nd August. That image of the 22nd would not install Ubuntu because not being able to set a file system. But I was trying to install on a btrfs format partition. So, it was not a standard installation. I have yet to try it with Ext4.

There are two stages to reporting bugs in daily images.

1) Finding the bug number of an already reported bug or reporting a new bug on Launchpad.
2) Reporting the test on QA tracker as a fail and including the bug number.

[http://iso.qa.ubuntu.com/](http://iso.qa.ubuntu.com/)

[https://help.ubuntu.com/community/ReportingBugs](https://help.ubuntu.com/community/ReportingBugs)

Here is a list of all bugs reported against Ubiquity

[https://bugs.launchpad.net/ubuntu/+source/ubiquity](https://bugs.launchpad.net/ubuntu/+source/ubiquity)

Another way is to see what bugs other have reported against the daily ISO images. These are the bugs reported against Alpha 2 images which do not include Ubuntu as it did not have an alpha 2 image. But it gives you an idea of what I am talking about. It is the bug numbers that are useful.

[http://iso.qa.ubuntu.com/qatracker/milestones/299/builds](http://iso.qa.ubuntu.com/qatracker/milestones/299/builds)

Regards.

---

### Post by thotz on 2013-08-24
> **startas said:**
> So, first bug is very big and buggy global menu bar in installation, it takes half of my screen, so you have to "try ubuntu", and then you can run install from there, otherwise you just cant see any buttons because of gigantic global menu bar, plus vsync is missing from installation too - these bugs are a 3-4 weeks old.
P.S. intel hd graphics.

Another bug appeared from day 22 and newer daily isos - when you boot into live mode to install ubuntu and press the install icon in dash, nothing happens - no error, no setup window.

Dont know how to reports bugs otherwise,  because ubuntus integrated bug reporting system never ever works, just crashes since 80's :)

Can confirm: I tried Ubuntu saucy-desktop-amd64 daily (23-Aug-2013 08:18) doesn't install in live cd mode.

---

### Post by thotz on 2013-08-28
I have installed Ubuntu saucy (28.August) today. It worked with my Ivy Bridge i5 3210M with Intel HD Graphics 4000. Yes I can see still this global big menu bar. Have you already filed a bug?

---

### Post by mc4man on 2013-08-28
> **thotz said:**
> I have installed Ubuntu saucy (28.August) today. It worked with my Ivy Bridge i5 3210M with Intel HD Graphics 4000. Yes I can see still this global big menu bar. Have you already filed a bug?
probably here, almost a month old
[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1207890](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1207890)

---

### Post by thotz on 2013-08-29
Thanks mc4man, I'll add me to this bug report.

---

### Post by carmonacr75 on 2013-08-31
Thank you for reading this, God bless you and I hope you are well! I  have just taken the plunge and quit Win8 cold turkey and enjoying Ubuntu  for its simplicity. I am a total newb and I know this is for pros but I would like to learn this version because I feel brave!   I have found how to update my aplications with  software updater and with terminal.  I am running Saucy Salamander Ubuntu 13.10 AMD  64, I chose it because I liked the name lol.   The following  errors occur:
Terminal; sudo apt-get update gives these 404s:
W: Failed to fetch [http://ppa.launchpad.net/deluge-team...amd64/Packages]("http://ppa.launchpad.net/deluge-team/ppa/ubuntu/dists/saucy/main/binary-amd64/Packages")  404  Not Found
W: Failed to fetch [http://ppa.launchpad.net/deluge-team...-i386/Packages]("http://ppa.launchpad.net/deluge-team/ppa/ubuntu/dists/saucy/main/binary-i386/Packages")  404  Not Found
E: Some index files failed to download. They have been ignored, or old ones used instead.
Where should I go to update these in saucy?  Can you point me to terminal commands to redirect update to the right place for updates?  Please be patient I love chalanges and I fell in love with "The Saucy Salamander!":lolflag:
Software update gives me some errors but I will post that later in this forum.

---

### Post by cariboo on 2013-08-31
You are getting the 404, because the latest version of Deluge is for Quantal, and when you setup the ppa, it probably was set for saucy. Go to System Settings->Software & Updates, then click the Other Software tab, highlight the deluge ppa, and click Edit. Change the Distribution to Quantal and click OK. Now running apt-get update should complete without any errors.

BTW, I used to be a Deluge user, but found qBitorrent suits my style of usage better.

---

