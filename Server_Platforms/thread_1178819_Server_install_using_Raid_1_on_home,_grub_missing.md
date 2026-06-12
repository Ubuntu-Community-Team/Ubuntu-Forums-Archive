---
title: "Server install using Raid 1 on home, grub missing?"
date: 2009-06-04
forum: Server Platforms
---

### Post by bertmanphx on 2009-06-04
Hello,
I have a ubuntu Server 9.04 disk, and have been trying to install it on a machine to use as a server.  Here's the setup:

sda - 500GB sata
sdb - 500GB sata
sdc - 320 GB eide, paritioned to /boot, / , /swap, /backup
sdd - 160 GB eide, /media/music

I go through the text based install and have no problems with the partitioning, and making the two sata drives act as a raid 1, using Linux's software raid and setup as /home

The install goes fine, but grub says it installs to (hd0).

When I reboot grub does not come up.  where the hell does Grub go?

I have tried the same install and marking /boot with the "boot flag", and without.

where the heck does it put grub?  and, how to I fix it.  

btw, I do have the bios going to the 320GB to boot first...

Now that my hard drive is setup, I thought about using the standard install CD and the gui, but I don't know if it will recognize the linux raid on the 500 GB drive?

Any help would be appreciated.

bertmanphx

---

