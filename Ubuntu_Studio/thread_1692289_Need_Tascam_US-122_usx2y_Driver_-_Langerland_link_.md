---
title: "Need Tascam US-122 usx2y Driver - Langerland link is gone!"
date: 2011-02-21
forum: Ubuntu Studio
---

### Post by danske on 2011-02-21
I have a tascam us-122 which I have had up and running for a long time in ubuntu studio, but I just did a computer rebuild / reinstall, and now the site which hosted the drivers is no longer up! All the tutorials point to the link:
[http://langerland.de/linux/usx2y/usx2y-fw-0.1b.tar.bz2]("http://langerland.de/linux/usx2y/usx2y-fw-0.1b.tar.bz2")
But it's no longer there, and I can't find it anywhere else...

I see plenty of people on here getting stuck at different points in the install process, and I was wondering if I could get someone to send me a copy of that driver so I can get back up and running.

As a thanks, I could host it on my web server and update the wiki pages so that we can all record beautiful tunes.  Deal?

Thanks,
Daniel

---

### Post by AutoStatic on 2011-02-21
You can find the driver here: [ftp://ftp.alsa-project.org/pub/firmware/](ftp://ftp.alsa-project.org/pub/firmware/)
I think your best bet is the 1.0.23 tarball. Further instructions here: [http://alsa.opensrc.org/Tascam_US-122](http://alsa.opensrc.org/Tascam_US-122)

Best,

Jeremy

PS I don't own a US122 myself.

---

### Post by DatBugler on 2011-02-21
AutoStatic, I don't think that's the same thing as the dead link. The USX2Y driver is what is missing, not the ALSA firmware loaders. As you can see [here](https://help.ubuntu.com/community/TASCAM_US-122), both are needed.

---

### Post by AutoStatic on 2011-02-22
The driver/firmware is in the alsa-firmware tarball, the ld2-ezusb.hex file from the Langerland tarball equals the tascam_loader.ihx file from the alsa-firmware tarball afaics.

Best,

Jeremy

---

### Post by _oscar_ on 2011-02-25
I use a US-122 for my 'mobile' studio (laptop with UbuntuStudio 10.10).
In case you have troubles finding the right stuff; attached is all I needed

---

### Post by AutoStatic on 2011-02-25
```
diff -Nru tascam_loader.ihx ld2-ezusb.hex > us122.diff
``` yielded a 0kb file so you don't need the Langerland tarball anymore.

Best,

Jeremy

---

### Post by _DRoboto on 2011-02-27
Hi guys,

I've been working on switching my audio laptop from Win7 to Linux (mostly use audacity and my tascam us-122) the machine is a custom laptop built on an msi gx720 mb so ubuntu recognises it as a gx720.  I've got maverick loaded, and upgraded with all the studio packages (except usplash because of a repository issue but it's just a theme so I don't think it matters) 
I've been following the same tutorial referenced above in this thread, but when I get to step 5 and run lsusb I get no indication that the system recognises the us-122 all the usb buses show up but they are all listed as device 001 ID 1d6b:001 Linux Foundation 1.1 root hub bus 1 and 2 show 2.0 root hub.  Yes the us-122 is connected via usb to the laptop.  
when I try to forge ahead (because I know the jack it's in is either bus 007 or 008 ) and run fxload for the stage two firmware it says "can't modify CPUCS: Broken pipe"

any insight would be greatly appreciated I'm good with computers but I'm a Linux n00b.

Thanks,

Mark

---

### Post by _DRoboto on 2011-03-12
Well after enough research and time in terminal I've got everything working quite well, and I have been really happy with Ubuntu studio for audio work.  Although it really does need to be running a real time kernel, but that was pretty easy to set up.

I put together a couple tips that cover the things I got hung up on here:
[http://ubuntuforums.org/showthread.php?t=1705291](http://ubuntuforums.org/showthread.php?t=1705291)

mark

---

### Post by DatBugler on 2011-03-12
> **AutoStatic said:**
> The driver/firmware is in the alsa-firmware tarball, the ld2-ezusb.hex file from the Langerland tarball equals the tascam_loader.ihx file from the alsa-firmware tarball afaics.

Best,

Jeremy

Thanks. It works fine now.

---

### Post by Wavebourn on 2011-10-21
> **_oscar_ said:**
> I use a US-122 for my 'mobile' studio (laptop with UbuntuStudio 10.10).
In case you have troubles finding the right stuff; attached is all I needed

I am getting an error trying to compile that thingy:

root@studio:~/tascam/usx2y-fw-0.1b# make
as31 ld2-ezusb.asm
including file: an2131.asm
Begin Pass #1
incLineCount=88
Warning, line -87, syntax error near "".
Errors in pass1, assembly aborted
Errors in pass2, assembly aborted
make: *** [firmware] Segmentation fault
root@studio:~/tascam/usx2y-fw-0.1b# ls
an2131.asm  COPYING  ld2-ezusb.asm  ld2-ezusb.hex  Makefile  README
root@studio:~/tascam/usx2y-fw-0.1b#

I use freshly installed Ubuntu 11.11

---

