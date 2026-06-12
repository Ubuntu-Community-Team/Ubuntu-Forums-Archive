---
title: "Intel DH61BE Marvell SATA 88SE917X on Ubuntu 10.04.3 LTS"
date: 2011-11-11
forum: Server Platforms
---

### Post by cphuntington97 on 2011-11-11
My mainboard is Intel DH61BE, which has two Marvell SATA ports 88SE917X which are (apparently) invisible to Linux Ubuntu 10.04.3 LTS.


uname -a: Linux fs4 2.6.32-35-generic #78-Ubuntu SMP Tue Oct 11 16:11:24 UTC 2011 x86_64 GNU/Linux

I tried adding: GRUB_CMDLINE_LINUX="ahci.marvell_enable=1" to /etc/defaults/grub but then the machine hangs on boot.

Any help?

---

### Post by cphuntington97 on 2011-11-14
Here is what transpired:

The mainboard has options for IDE or AHCI for the secondary controller. It shipped set to "IDE" and, thinking that would be my most compatible option, I left it as such.

I tried setting it to AHCI but then my Ubuntu Live CD wouldn't boot, so I figured that was no good.

However, I wanted to use the extra controller and after installation set AHCI in the bios and - viola- now it seems to work. I suppose I don't need a special Marvell sata driver after all.

But there is a catch - the only way I can get my machine to boot right now is to boot to cd and select "boot from first hard drive".

grub2 reinstalled with no errors however it still doesn't boot in AHCI mode. If I revert to IDE mode I lose two SATA controllers.

Help...?

---

### Post by cphuntington97 on 2011-11-14
I updated to the 10/18/2011 main board firmware and still no dice.

Some options I thought of... 

1. Fix grub 
or 
2. Boot from a flash drive

any thoughts?

---

