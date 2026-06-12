---
title: "Dual Boot to VirtualBox, Grub Problem"
date: 2008-05-09
forum: Virtualisation
---

### Post by jeremymiles on 2008-05-09
Hi All,

I've got a dual boot system, which uses the Grub boot loader to select the OS.

I've installed VirtualBox, and set up the virtual machine, using the already existing Windows partiiton.

When I try to start the virtual machine, it doesn't start Windows, it starts the boot loader, which says "Error 21" and stops.

Is it possible to do this, or do I need to remove the boot loader?

Thanks,

Jeremy

---

### Post by DaxPod on 2008-06-02
I am having the same problem as well.  Two separate hard drives.  Vista on one and Ubuntu Hardy on the other.  I get Error 21 when I try to load the virutal machine.  Any ideas?

Dax

---

### Post by moaxey on 2008-07-02
i get this too (although error 17)

it must be that the scheme of hd0.0
is different when booting through a .vmdk image from a real partition

i guess theres no help on this forum as you have to have the non-free version of virtualbox to use this function, which doesnt come through ubuntu.

now if I could only remember how to get the grub prompt to come up when booting the virtual machine, and then be able to see whats connected and choose a boot partition manually...

---

### Post by Tankerdog2002 on 2008-08-13
Same here. Error 21
Here's a fdisk on my drives, if that helps.

[[]][[]][[]][[]][[]]
ronnie@Dell-Vostro-400:~$ fdisk -l

Disk /dev/sda: 160.0 GB, 160000000000 bytes
255 heads, 63 sectors/track, 19452 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe891e891

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       19451   156240126    7  HPFS/NTFS

Disk /dev/sdb: 160.0 GB, 160000000000 bytes
255 heads, 63 sectors/track, 19452 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x2fda2fd9

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       18657   149862321   83  Linux
/dev/sdb2           18658       19452     6385837+   5  Extended
/dev/sdb5           18658       19452     6385806   82  Linux swap / Solaris
ronnie@Dell-Vostro-400:~$
[[]][[]][[]][[]][[]]

The "error 21" leads me to believe that Vbox does not see the created mbr and is attemping to mount from a normal GRUB. But I 'dunno.

Anyone got a clue on this one?  "Yikes!"

---

### Post by Sand Lee on 2008-11-22
Try using the [grub manual]("http://www.gnu.org/software/grub/manual/html_node/Making-a-GRUB-bootable-CD_002dROM.html") to make a boot cd to your windows partition. There's an easier version of the manual on [my tutorial.]("http://ubuntuforums.org/showthread.php?t=769883")

---

### Post by crosslink on 2009-03-05
I had the same problem and fixed it like so...

[http://blog.nixternal.com/2008.02.29/virtualbox-and-grub-issue/](http://blog.nixternal.com/2008.02.29/virtualbox-and-grub-issue/)

---

