---
title: "Booting gutsy CDROM on SPARC Blade 1500/2500"
date: 2007-10-23
forum: Sun Sparc Users
---

### Post by torches on 2007-10-23
I am having a problem booting gutsy CDROM on a SPARC Blade 2500. sometimes I am getting an error on  other cases it reboots to the ok prompt ( I have auto-boot set to false). 

For some weird reason I was never able to boot an ubuntu CDROM on a sparc machine. is it that difficult?

---

### Post by zanderred on 2007-10-25
Hi, when you first boot the computer the memory is initialized press stop a befor initializing finnises, not after.

---

### Post by flamtech on 2007-11-06
> **zanderred said:**
> Hi, when you first boot the computer the memory is initialized press stop a befor initializing finnises, not after.

Anyone have any other Ideas?  I'm not able to boot Gutsy with my blade 2500 either.  It gets to loading the initial ramdisk (or starting the kernel) and then reboots.  One of the errors was a memory alignment error just before loading the ramdisk.

---

### Post by robertmazur on 2007-11-06
Not to jump the bandwagon, but same here on a Blade 1000.  I get:

boot:
Allocated 8 Megs memory at 0x40000000 for kernel
Loaded kernel version 2.6.22
Loading initial ramdisk (.....string of mamemory address)
Memory Address not Aligned.
{0} ok

I am pressing STOP A as soon as I see the memory initializing, give a boot cdrom, and then I get the "Welcome gutsy!" screen....then the text above.

Rob

---

### Post by drosky on 2007-11-06
I had this problem on my SB 150's.  There have been some other threads about it, but probably under titles that don't hint at the same problem.  The problem is that the Ubuntu CDROM won't boot properly after hitting STOP-A if Solaris is installed (don't know exactly why).  The solution is to change the boot device sequence so that the system will directly boot off the cdrom.  After hitting STOP-A and getting the boot ROM prompt, type the following command:

[FONT="Courier New"]setenv boot-device cdrom disk net[/FONT]

Then reboot the system with the Ubuntu cdrom in the drive.  It should then boot OK (at least it did for me on the SB 150's)

> **robertmazur said:**
> Not to jump the bandwagon, but same here on a Blade 1000.  I get:

boot:
Allocated 8 Megs memory at 0x40000000 for kernel
Loaded kernel version 2.6.22
Loading initial ramdisk (.....string of mamemory address)
Memory Address not Aligned.
{0} ok

I am pressing STOP A as soon as I see the memory initializing, give a boot cdrom, and then I get the "Welcome gutsy!" screen....then the text above.

Rob

---

### Post by westfall@computer.org on 2007-11-21
The memory alignment error you see when loading the RAM disk is an address conflict with the floppy drive memory range.  Disconnect your floppy drive.  This worked for me on my Sun Blade 2000 and Ultra 60.  I have seen this in both Feisty fawn and Gutsy.  It's worked both times. I reconnected the drive just be to sure that the floppy was the issue with booting the CD and received the same alignment error.

---

### Post by randolf_carter on 2008-07-09
> **drosky said:**
> I had this problem on my SB 150's.  There have been some other threads about it, but probably under titles that don't hint at the same problem.  The problem is that the Ubuntu CDROM won't boot properly after hitting STOP-A if Solaris is installed (don't know exactly why).  The solution is to change the boot device sequence so that the system will directly boot off the cdrom.  After hitting STOP-A and getting the boot ROM prompt, type the following command:

[FONT="Courier New"]setenv boot-device cdrom disk net[/FONT]

Then reboot the system with the Ubuntu cdrom in the drive.  It should then boot OK (at least it did for me on the SB 150's)


Thanks a lot!!!, I was googling too much. Now my gentoo (forgive me :) boots on a sunblade 150.

Now i have ssh, scp, etc... for backing up / clone my old workstations.

---

