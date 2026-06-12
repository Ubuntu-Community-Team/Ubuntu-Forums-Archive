---
title: "grub loader detects Windows 7 but would not boot it"
date: 2015-01-12
forum: Ubuntu/Debian BASED
---

### Post by snitz2 on 2015-01-12
I have 2 HDDS.

1: SSD 240GB on which Windows 7 is installed
2: HDD 1TB for storage that I shrinked and created a separate 100GB partition from with swap.

I installed BackBox 4 on the 100GB parition while leaving the SSD and windows intact.

I installed BB's bootloader on Windows 7 recovery partition (I don't know if that was the correct choice)

Now on the boot menu, I get "Windows 7" option but when I select it, it just reloads the boot menu and asks me to choose again.
It won't let me into Windows.

/dev/sda4/: BackBox 4
/dev/sda3/: Swap
/dev/sda2/ Storage
-
/dev/sdb1/: Windows

I edit grub.cfg and replaced
```
menuentry 'Windows 7 (loader) (on /dev/sda1)' --class windows -
```

With /dev/sdb1/ and ran --sudo update-grub and restarted.

Still the same error.

I also tried adjusting the "hd0" to whatever number my HD has.

I tried from 0 to 3, none worked.

```
menuentry 'Windows 7 (loader) (on /dev/sdb1)' --class windows --class os $menuentry_id_option 'osprober-chain-0886FE9886FE858A' {
        insmod part_msdos
        insmod ntfs
        set root='hd0,msdos1'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  0886FE9886FE858A
        else
          search --no-floppy --fs-uuid --set=root 0886FE9886FE858A
        fi
        parttool ${root} hidden-
        chainloader +1
}
```

On windows partition it says "hd0.msdos1" while on the rest it says "msdos4"
Is it somehow related?

---

### Post by yancek on 2015-01-12
> I installed BB's bootloader on Windows 7 recovery partition (I don't know if that was the correct choice)

Nope, definitely not.  You might have overwritten some necessary information on that partition.  
Use a terminal in Backbox and run this command as root user:  fdisk -l(Lower case Letter L in the command)  If that doesn't produce any results run:  sudo fdisk -l
Post that output here as well as the output of:  blkid or if that doesn't work:  sudo blkid
That will give us some idea of which partitions are windows as well as their uuid.

---

### Post by snitz2 on 2015-01-12
This is the output of "fdisk -l"

```
root@Base:/# fdisk -l

Disk /dev/sda: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x0e092a46

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      206847      102400    7  HPFS/NTFS/exFAT
/dev/sda2          206848  3679698943  1839746048    7  HPFS/NTFS/exFAT
/dev/sda3      3679700990  3698130678     9214844+   f  W95 Ext'd (LBA)
Partition 3 does not start on physical sector boundary.
/dev/sda4      3698130944  3907025475   104447266   83  Linux
/dev/sda5      3679700992  3698130678     9214843+  82  Linux swap / Solaris

Disk /dev/sdb: 240.1 GB, 240057409536 bytes
255 heads, 63 sectors/track, 29185 cylinders, total 468862128 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x6a33ae40

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1            2048   468858879   234428416    7  HPFS/NTFS/exFAT


```

And this is the output of "blkid"
```
root@Base:/# blkid
/dev/sda1: LABEL="System Reserved" UUID="0886FE9886FE858A" TYPE="ntfs" 
/dev/sda2: UUID="948CA6D08CA6AC64" TYPE="ntfs" 
/dev/sda4: UUID="3b8e1432-345b-4166-af34-90c550313950" TYPE="ext4" 
/dev/sdb1: LABEL="Windows" UUID="7C626A1E6269DE00" TYPE="ntfs" 
```

---

### Post by oldfred on 2015-01-12
Moved to Other OS since not Ubuntu.

With two drives and installs on separate drives, you should have Windows boot loader on SSD and grub2's boot loader on the MBR of your hard drive.
You never install grub2's boot loader to a NTFS partition. Windows has essential boot info in the partition boot sector. Your probably cannot boot into recovery partition. But if you made the recovery set of DVDs already as recommended as soon as you start computer,  then it does not matter.  If not you may be able to use testdisk to restore a backup of the partition boot sector.

---

### Post by snitz2 on 2015-01-12
Ok, so I understand there's no way to fix this.

At this point, I have made a backup of everything and I do not mind formatting and reinstalling Windows 7.
I just need it to be able to run Photoshop and Premiere.

My concern is Windows will overwrite ubuntu's grub loader and would not detected BackBox.

---

### Post by oldfred on 2015-01-12
If you want to be sure, you can always disconnect one drive and do an install to it. Then only connect the other drive and do an install to it.
Grub2 has os-prober which runs with sudo update-grub which when both drives are plugged in should find Windows. 
But with the version you use, I do not know if all the software is there, with Ubuntu it rarely is an issue.

---

### Post by grahammechanical on 2015-01-15
For information: with Grub

hd0 = first hard disk. What Linux would call sda.
msdos1 = first partition.
msdos4 = fourth partition.

So, hd0,msdos1 = sda1 and hd0,msdos4 = sda4. Grub uses a different naming system to Linux.

Regards

---

