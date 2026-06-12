---
title: "Upgrading XP+Lucid to Win7+Raring"
date: 2014-01-09
forum: Windows
---

### Post by ofnuts on 2014-01-09
The family computer was getting a bit old so the hardware got upgraded for Xmas (new CPU+MB+RAM+GPU+HDD).

I am now upgrading the software. The older system was dual-booting WinXP+Lucid; The new one will have to dual boot Win7+Raring, from a new HDD. The two HDDs (old 500GB + new 2TB) may coexist for a while but eventually the old one will be removed.

The motherboard is a Gigabyte Z77-DS3H with BIOS F9 (2012-09-19). I also have two optical drives.

This is the family computer, so it has regular users who can have critical needs so I'm trying to migrate things without creating a usage interruption. Ideally I can install everything on the second disk and give it some testing while the machine multiboots on all disks. 

Now for the questions:

1) i can't find an option to set the boot order between the HDDs. The BIOS lets me specify the optical drives individually but the HDDs seems to be lumped together under "Generic storage 0551". How is the boot order determined? By SATA connector precedence? Or is it because one of these (the new one, likely) has not got a usable MBR?

2) I seems that the HDD can be run in either plain SATA or AHCI mode. Is there a good reason for AHCI? Is this settable per disk/OS? Or can I switch it on later when the old disk is removed?

3) A first attempt to install Win7 on the 2TB worked, but the initial Grub screen is now replaced by a Windows screen asking if I want to boot Win7 or the previous version of Windows (this boots XP, so GRUB has been disabled).

4) I'm a bit lost about the current boot sequence, it is obviously still booting on the old disk because if I remove it it asks me to specify a bootable device.

What are my options now? disconnect the old disk, install Win7+Raring on the new (that should make it bootable), and either hope I can switch boot order in the BIOS while the disks coexist or I can make the new Grub pick both Win7 and WinXP? Something else?

---

### Post by CharlesA on 2014-01-09
The boot order for the hard drives should be in the advanced section of the BIOS.

---

### Post by ofnuts on 2014-01-10
That's also what I thought, alas.

---

### Post by monkeybrain20122 on 2014-01-10
Raring is going to reach end of life on the 27th this month. there is no point in installing it now. Either 12.04 or 13.10.

---

