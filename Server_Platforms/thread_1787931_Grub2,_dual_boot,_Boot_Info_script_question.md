---
title: "Grub2, dual boot, Boot Info script question"
date: 2011-06-21
forum: Server Platforms
---

### Post by lister171254 on 2011-06-21
I've run the Boot info script and am curious why I can boot despite the error the script reports.

-----------------------
                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.97-1.98) is installed in the MBR of /dev/sda and looks at sector 
    1 of the same hard drive for core.img. core.img is at this location and 
    looks in partition 1 for (,msdos1)/grub.
 => No boot loader is installed in the MBR of /dev/sdb.
 => Grub2 (v1.97-1.98) is installed in the MBR of /dev/sdc and looks at sector 
    1 of the same hard drive for core.img. core.img is at this location and 
    looks in partition 1 for (,msdos1)/grub.
 => No boot loader is installed in the MBR of /dev/sdd.

sda1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  Grub2 (v1.97-1.98)
    Boot sector info:   Grub2 (v1.97-1.98) is installed in the boot sector of 
                       sda1 and looks at sector 273599 of the same hard drive 
                       for core.img, but core.img can not be found at this 
                       location.
    Operating System:  
    Boot files:        /grub/grub.cfg /boot/grub/grub.cfg /grub/core.img 
                       /boot/grub/core.img

sda2: __________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:   mount: unknown filesystem type ''

sda3: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda4: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        

sdb1: __________________________________________________________________________

    File system:       linux_raid_member
    Boot sector type:  -
    Boot sector info:  

sdc1: __________________________________________________________________________

    File system:       linux_raid_member
    Boot sector type:  -
    Boot sector info:  

sdd1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        

md0: ___________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img
------------------------------------------------------------

---

### Post by oldfred on 2011-06-22
Are you concerned about the grub installed to the partition boot sector of sda1? Grub does not normally use an install to a partition and in fact makes it difficult to install to a partition if you try manually. They still seem to let you install grub2's boot loader anywhere on a new install with the combo box.

All MBR (msdos) computers boot from the BIOS, to the MBR, to additional code. Windows use MBR to determine which primary partition has boot flag (active partition) and jumps there for more code. Grub2 does not normally use the partition boot sector but has additional code just after the MBR that finds the grub folders and uses the grub files.

Grub or BIOS also misreport drive. So same drive is not always same drive. Mine says same drive for sda, but actually boots correct partition in sdc. I only have 4 partitions in sda and am booting sdc13 so it is obvious that same drive is not correct. 

The newer grub 1.99 and latest version of script identify it more correctly as it shows UUID that it uses to find correct boot partition.

---

### Post by lister171254 on 2011-06-22
I'm just concerned that the script reports that core.img cannot be found on sda1, when it's (clearly) there.

My real problem is that I cloned sda as it had some sector problems (not fatal yet), but when I tried to boot of the cloned disk, booting into Windows 7 works fine, but booting into Linux gives me an error:

error: file not found
error: you need to load the Kernel first.

I just want to make sure that my original boot disk is in correct order.

---

### Post by lister171254 on 2011-06-22
More info about my config.

I've got /boot and Windows 7 on one disk with "/" on a RAID1.

While grub finds "/" on the original, It doesn't on the cloned disk (I guess)

---

### Post by YesWeCan on 2011-06-22
> **lister171254 said:**
> I'm just concerned that the script reports that core.img cannot be found on sda1, when it's (clearly) there.
It isn't enough for the core.img file to be in sda1, it also has to be located at the correct sector address. The Grub boot code cannot search a filesystem tree so it relies on a fixed address. Various things can cause the sector address of a file to change. So at some point core.img location may have changed   alienating it from Grub's boot code in the PBR. The Grub installer discourages partition installations for this reason.

This is not a problem at all because you are not using either of these to boot. You are using a different Grub boot code in the MBR and a different core.img just after the MBR.

> My real problem is that I cloned sda as it had some sector problems (not fatal yet), but when I tried to boot of the cloned disk, booting into Windows 7 works fine, but booting into Linux gives me an error:

error: file not found
error: you need to load the Kernel first.

I just want to make sure that my original boot disk is in correct order.
If you get a Grub menu and can boot Windows the problem is not with Grub. It's more likely an fstab entry problem that is preventing the root partition from being mounted. It depends how you went about cloning the disk.

It would help to see the whole of the bootinfoscript output as it shows fstab and your device block IDs.

---

### Post by lister171254 on 2011-06-22
I think I worked it out. 

When I had a closer look at the option before booting (by choosing e at the at the menu section) I realised that the original system boots kernel 2.6.35.30, while the cloned system boot 2.6.31.17!!!! That kernel doesn't exists anymore on my system

How is this possible? After trawling the net for two days I found a note saying that grub.cfg is the only file that gets copied during the cloning. How does Clonezilla know where it is; the note said that clonezilla searches all partitions for a grub.cfg file (no indication what happens when you have more than one for some reason).

So I went back and booted into my working system and found that I had 2 grub.cfg files

One in /boot/grub (the one the working system uses)
One on /boot/boot/grub (the dud one)

Ignoring the reason as to why there is a /boot/boot/grub directory, I have now removed that directory so there is only on grub.cfg file.

I will clone this disk again and will let you know the outcome, but am pretty sure it will work.

---

### Post by lister171254 on 2011-06-23
I can confirm that deleting the obsolete grub.cfg before cloning fixed the problem as I'm posting this from the cloned systems.


I'll post this as a Clonezilla bug

Thanks for your help.

---

