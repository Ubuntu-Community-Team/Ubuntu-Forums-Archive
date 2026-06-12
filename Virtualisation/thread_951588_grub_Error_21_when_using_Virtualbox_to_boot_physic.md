---
title: "grub Error 21 when using Virtualbox to boot physical partition"
date: 2008-10-18
forum: Virtualisation
---

### Post by Roig on 2008-10-18
I installed Virtualbox 1.6.6 on ubuntu hardy heron. I have Windows XP installed too, and i want virtualbox to acces the winxp partition. 

i did:

```
dani@ubuntudani:~/.VirtualBox$ fdisk -l

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x61a261a2

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       60800   488375968+   7  HPFS/NTFS

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000776bc

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       29644   238115398+  83  Linux
/dev/sdb2           29645       30401     6080602+   5  Extended
/dev/sdb5           29645       30401     6080571   82  Linux swap / Solaris
dani@ubuntudani:~/.VirtualBox$ 

```

looking at fdisk i think the command to create the vdmk file is this:

```
VBoxManage internalcommands createrawvmdk -filename ~/.VirtualBox/SystemHD.vmdk -rawdisk /dev/sda -partitions 1 -register

```

Well, i did it, and started virtualbox with the SystemHD.vmdk but when i start the virtualization it says: 

```

GRUB Loading, please wait: 
Error 21

```

And it doesnt show me the menu :(. I can't find a solution. Maybe anyone with more experience can point me what i'm doing wrong please? 

Thanks!


P.D. Sorry about my english!

Ah, btw my drive is SATA.

---

### Post by Roig on 2008-10-19
Anyone? Please?!:confused::confused:

---

### Post by b0b138 on 2008-10-20
Did you see this thread, [http://ubuntuforums.org/showthread.php?t=769883](http://ubuntuforums.org/showthread.php?t=769883)

---

### Post by Roig on 2008-10-20
Yes b0b138 i saw this thread, and it was the thread that i followed.

It seems that all is ok, because when i start the virtualization, in the virtualbox screen says: "Loading grub..", but then it launch the faaacking Error 21. 

I don't know what i have to do.

---

### Post by b0b138 on 2008-10-21
Well error 21 means grub cant find the disk. But, according to the tutorial, there shouldn't be a grub menu.  Maybe try going through the first couple of steps again to check that you pointed everthing to the right place.

---

### Post by eternaluxe on 2008-10-21
Have you enabled IO APIC and VT-x/AMD-V for the windows virtual machine?

---

