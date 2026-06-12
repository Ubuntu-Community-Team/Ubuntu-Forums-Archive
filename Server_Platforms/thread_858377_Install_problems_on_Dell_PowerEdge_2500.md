---
title: "Install problems on Dell PowerEdge 2500"
date: 2008-07-13
forum: Server Platforms
---

### Post by King of Hearts on 2008-07-13
I cannot get Ubuntu, Server Edition (32-bit) installed on my PowerEdge 2500.

My CD has been validated, my checksums match, but still it will not install properly.  The process stops during package installation, usually around 2% or 6%.

I have used both fast burns (52x-48x) and slow burns (4x-2x), but still the disk cannot be validated nor installed on the server.  I have been able to validate the disk on a different unit, however.

I suspect the disk drive is faulty, but I have not been able to locate a replacement.

The option to enable OS installation has been switched on in the BIOS already, and all BIOS options are correctly set.

---

### Post by Dangerousdave26 on 2008-08-09
I have the same problem and have joined hoping to find an answer to the problem. I do not belive it is a CD Rom problem. I think it is more like a CD driver problem in the installer that does not understand the CD Rom. 

I am able to load a Windows OS on my server with out a problem it is only when I try and load Ubuntu server that I get the CD Rom read failure. It usually gets to 2-12% and dies.

I tried down loading from three different locations and burnt three different Disks and no joy.

I am however burning the ISO to a RW CD and I don't know if that could be the problem.

---

### Post by windependence on 2008-08-09
You don't want to switch on that option to install an OS. That is very misleading. It just limits your physical memory to 256 MB which will definitely kill your install. Set it to OFF. This option is for special operating systems that must have a small amount of RAM to install.

-Tim

---

### Post by windependence on 2008-08-09
Sorry, double post. :)

---

### Post by Dangerousdave26 on 2008-08-10
Problem solved 

I had to purchase a PCI IDE Controller card and connect an old 52X Cdrom that I had in an old Win98 box. The bios recognized it and put it in the boot list at the end. I moved it to first place and the system booted to the CD and started the install. It failed to continue the install after I selected the language then clicked Install server. 

I had to put a CD in the old drive that would not read all of the files and one in the new drive I installed. I booted to the old drive until It prompted me for the key board lay out then I took out the old drives cd. 

It found the new drive and continued loading from there. Now the learning part starts.

---

### Post by King of Hearts on 2008-08-10
Thank you SO much!

I think turning the OS install off WILL solve my problem, can't believe I didn't try that before.

EDIT:  I guess not!

I'll go grab a PCI IDE card then.

---

### Post by cariboo on 2008-08-10
IF your problem isn't solved you could always try the mini.iso this will install just enough to get you running to do a network installation.

The mini.iso is avalable here:

[https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)

Jim

---

### Post by King of Hearts on 2008-08-10
Thanks!  I'll try this...

EDIT:  It worked!  Thanks so much!

Mini ISO is win!

---

### Post by djpenn3 on 2008-09-28
Greetings all. Lots of folks are having the same problem, and I don't think it's been resolved yet. The Launchpad bug is here:[https://bugs.launchpad.net/dru/+bug/148466]("https://bugs.launchpad.net/dru/+bug/148466"). My work-around was to install a PCI IDE controller and standard CD-ROM and boot/install from that. Hope this saves some people some frustration.

Cheers,

Dave Penn

---

### Post by ripperzane on 2009-01-03
I have a Dell Power Edge 2550: 2x Intel PIII 933.
I got this second hand, so the only Scsi drive I had initially is an old 18.4 68 Pin 160 laying around. I installed it in the 5th slot (waiting for the ebayed HDD Hotswap 80 pins still) and have run into a couple of snags. My intention to have the 5th slot filled with the OS, and use the drives I obtain for multiple lab setups for future deployment plans which are software centric, not hardware, which is where this server SHOULD come in handy...
I ran into the Scsi CDrom not loading the standard ISO.
After using the Mini.iso for the latest versions of both 8.04.1 and 8.10, I keep having I/O issues. I suspect the drive for the latter issue, and I am aware of the former of the scsi drive not working with whole install disks (standard downloaded ISO, and yes I have multidownloaded and burned them at varying speeds multiple times, all passing checksum om md5checksum on my desktop/laptop and even working in a virtualbox boot which I did "check disk" option.
This post is just to state the issues I am running into for others to see.
I am thinking the I/O with the auto partitioning is possibly the HDD, but I am able to fdisk/cfdisk it and able to mk2fs.ext and create a swapon and all that. SOOOO.... question is, why is the installer erroring on the mini.iso?


I am at an empass, and am hoping to not have to go with another OS, as to that Ubuntu is to be the cornerstone which all this depends... specifically Ubuntu.

ANy help would be greatly appreciated.
Regards,
RZ

---

### Post by Amarz2500sc on 2013-04-23
I have the same problem before turns out okay after i flash the bios to A07. Installation is a breeze. however upon boot. i got an error, cannot display this video mode. I'm still finding the solution for this. HELP PLS Anyone... I'm getting tired re-installing it over and over again..

p/s - Newbie in Ubuntu World.

---

### Post by darkod on 2013-04-23
Try booting into the recovery mode, instead of the normal mode. That should show is a recovery menu, select Drop to root shell.

Once you are in the shell, first remount / as RW:
```
mount -o remount,rw /
```

Then open /etc/default/grub for editing:
```
nano /etc/default/grub
```

Find the line saying like #GFX_MODE=640x480 and remove the # symbol in front. That will enable the line and set the resolution to basic 640x480 during the grub menu. Press Ctrl+O, Enter to save the change. Then press Ctrl+X to close nano.

Reboot with:
```
reboot
```

See if that helps it boot.

---

