---
title: "Bsod...... :("
date: 2007-06-01
forum: Windows
---

### Post by dextrone on 2007-06-01
Hello, I would appear to be #......... that has done a dirty shutdown and has resulted in a 0x24 stop/bsod; in other words, Windows is dumb, I can read my files via my linux live cd but winxp says they're corrupt {backed up my files already;they work}, and to run chkdsk /f.

I have a winxp-pro cd BUT !!! my hdd isn't detected in the setup OR recov. console; It's a sony Vaio VGC-RC110G*; probably needs a SC__{I don't know the last 2 characters} driver, but I still don't have a floppy !!!

What I have:
This linux live cd {kubuntu}
A Win XP CD
Acronis Disk Director/True Image

Any help?**

**ntfsfix doesn't work; tried several times

*I hate this computer; darn retail marketing; last time my ram was corrupt now I can't even use the recov. console on it; it doesn't even have a floppy drive; I have a lemon under warranty at best buy{which told me that there was a software prob. but [blabh,blabh,blabh]}

> 
[QUOTE]
hi, is it a sata drive? if so, do you have a sony recovery or driver disk that has the required driver? if not you may have to go to the sony support site and download them. if you don't have a floppy there may be instructions there about how to install them.

you could always, as you have your data backed up, forget about windows, install kubuntu, and if you feel the need, once you are familiar with linux, install virtualbox, and install a xp to run on top of kubuntu.

if you post the exact bsod error i could maybe help more, but there may be more qualified people available to help if you post in the 'windows' forum under 'other OS's', if you do this, please add a line to have this post deleted, thanks,

best of luck.Well; I still have the recovery partition .....

And thanks for the help; I can't believe how stupid M$ is; linux not even with real ntfs drivers does a better job than WINNT.

And it's a SCSI drive......[/QUOTE]

---

### Post by smoker on 2007-06-01
hi, dextrone,

have a look at this link regarding your BSOD error and see if it helps:
[http://www.techspot.com/vb/topic5352.html](http://www.techspot.com/vb/topic5352.html)

if you need xp or w2000 boot disks to try, you may get them here, i know these are for floppies, but there are option on bootable cd, also:
[http://www.bootdisk.com/](http://www.bootdisk.com/)

best of luck:-)

ps - i asked for your other posting to be removed to avoid confusion.

---

### Post by rickyjones on 2007-06-02
> **dextrone said:**
> Hello, I would appear to be #......... that has done a dirty shutdown and has resulted in a 0x24 stop/bsod; in other words, Windows is dumb, I can read my files via my linux live cd but winxp says they're corrupt {backed up my files already;they work}, and to run chkdsk /f.

I have a winxp-pro cd BUT !!! my hdd isn't detected in the setup OR recov. console; It's a sony Vaio VGC-RC110G*; probably needs a SC__{I don't know the last 2 characters} driver, but I still don't have a floppy !!!

What I have:
This linux live cd {kubuntu}
A Win XP CD
Acronis Disk Director/True Image

Any help?**

**ntfsfix doesn't work; tried several times

*I hate this computer; darn retail marketing; last time my ram was corrupt now I can't even use the recov. console on it; it doesn't even have a floppy drive; I have a lemon under warranty at best buy{which told me that there was a software prob. but [blabh,blabh,blabh]}

Sounds like you need the driver for your hard disk controller in order for Windows to read your drive. If you don't have a floppy drive you'll probably need to grab a USB Floppy drive and use that, then boot to the Windows CD and tell it that you have other drivers (hit F6 when it asks you to).

-Richard

---

