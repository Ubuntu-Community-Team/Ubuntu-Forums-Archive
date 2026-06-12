---
title: "Grub-Efi error with ubuntu (zentyal)"
date: 2013-02-26
forum: Server Platforms
---

### Post by deewanagan on 2013-02-26
Hello Everyone,

I was trying to install zentyal (ubuntu 12.04) on an IBM server. all the installation process goes smoothly except the boot installation. the server have several hard disks. i made a partition for /boot on the first disk, then created an LVM group from the rest of the Harddisks. in the LVM group, i created two lvm partitions one for / and the other for swap. no matter what i tried i couldn't make the boot install. it gives the grub-efi error. i used the rescue option to fix the problem with "boot-repair" program. it wasn't successful either(although i had already mounted the partitions in order to fix the grub). the [link]("http://paste.ubuntu.com/5567008/") shows the output of the boot-repair program. hope some body would be able to help.

thanks.

---

### Post by oldfred on 2013-02-26
I do not really know RAID nor LVM. But I do not think you can mix gpt partitions with MBR partitions within LVM?

It looks like you created a gpt drive and put a gpt drive boot flag on a boot partition which converts it to efi boot not a MBR boot partition.
> In GPT fdisk, ESPs have a type code of EF00. In libparted-based tools, you mark the ESP as such by setting its "boot flag." Note that the libparted "boot flag" means something entirely different under MBR, and you should not set the "boot flag" on any OS partition under GPT!

    

Is your UEFI/BIOS offer both UEFI & BIOS boot options? May be best to stay with BIOS and MBR partitioning.

With all these drives do you want LVM or really RAID?
       Advantages/Disadvantages LVM Post #9
[http://ubuntuforums.org/showthread.php?t=1586328](http://ubuntuforums.org/showthread.php?t=1586328)
lvm info older:
[http://ubuntuforums.org/showthread.php?t=141900](http://ubuntuforums.org/showthread.php?t=141900)
[http://tldp.org/HOWTO/LVM-HOWTO/index.html](http://tldp.org/HOWTO/LVM-HOWTO/index.html)
[http://tldp.org/HOWTO/LVM-HOWTO/benefitsoflvmsmall.html](http://tldp.org/HOWTO/LVM-HOWTO/benefitsoflvmsmall.html)

---

