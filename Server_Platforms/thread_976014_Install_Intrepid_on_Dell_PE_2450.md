---
title: "Install Intrepid on Dell PE 2450"
date: 2008-11-08
forum: Server Platforms
---

### Post by chainofcommand02 on 2008-11-08
Hi y'all. I'm trying to install Intrepid Ibex on a Dell Poweredge 2450. I've chosen keyboard layout, and the little details but then it asks me for what driver to use for my storage. Apparently it could not auto-detect what I need to use. My RAID controller is a Dell PERC 3/Si. I've read that this controller is made by Adaptec. So, does anybody know what I should use here? I think I have found the Windows drivers here, hope this link works for everybody: [Driver from Dell Website]("http://support.dell.com/support/downloads/format.aspx?c=us&l=en&s=gen&deviceid=1372&libid=35&releaseid=R74084&vercnt=3&formatcnt=0&SystemID=PWE_PNT_P3C_2450&servicetag=&os=WNET&osl=en&catid=-1&impid=-1") So I didn't know if there was something like "ndiswrapper" or something like that to use the Windows driver, or does somebody have any insight? Thank you everybody!! -chainofcommand02

---

### Post by darkray77 on 2008-11-10
I am actually in the exact same boat as you are.  I tried a fresh install of 8.10 on the box, and it appeard to install just fine.  When it restarts after the install, and starts into the boot loader (grub), I get an error from grub ...

Grub error 17

I'm going to investigate more, but I suspect that the scsi card bios needs to be upgraded.

---

### Post by CrucifiedEgo on 2008-11-10
As I recall with my 1650, I needed to update the SCSI Firmware because there was a bug with newer kernels(really, the bug was with the scsi firmware all along, but it was uncovered with the newer kerenels.  I digress...)  Try updating firware/bios/etc., installing windows briefly if you need to to do so.

---

### Post by darkray77 on 2008-11-10
> **CrucifiedEgo said:**
> As I recall with my 1650, I needed to update the SCSI Firmware because there was a bug with newer kernels(really, the bug was with the scsi firmware all along, but it was uncovered with the newer kerenels.  I digress...)  Try updating firware/bios/etc., installing windows briefly if you need to to do so.

Yea, I actually did just upgrade the system BIOS (version A09), and then the firmware for the Adaptec PERC3/Si SCSI card (version 2.8.1.609a, Rev A15) since it required system firmware A09).  I actually had to hunt up 4 floppies for this, creating a DOS bootable disk, and then swapping that out and running the .exe files from the other disks for the BIOS updates.

It claimed that both were successful, but then when I restarted the server, I ended up getting a "Plug and Play error" from the bios.  I'm not really sure what could be causing that, but I unplugged it, and left it sit for a while.  Maybe it's just the case that it needed to clear out the flash memory.

I'll be working on it more this afternoon, so I'll post how things went ...

---

### Post by chainofcommand02 on 2008-11-11
OK cool stuff, thanks for the replies. I'll look into updating the firmware on the SCSI controller, BIOS etc etc... And if it's all floppy based, yeah, I'll have to hunt for some myself!! haha. So I assume you just get the firmware updates from the dell.com "drivers and downloads" support section...?

And FYI, my situation is a bit different in that I haven't even fully installed 8.10 yet, it asked me for drivers during the install process and I got stuck at that point, because I don't know where to find the linux drivers for my RAID controller....

And finally, I like the BHM avatar!

---

