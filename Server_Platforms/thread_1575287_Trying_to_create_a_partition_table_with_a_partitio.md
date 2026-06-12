---
title: "Trying to create a partition table with a partition grater than 2TB fail with ubuntu"
date: 2010-09-15
forum: Server Platforms
---

### Post by shahansudu on 2010-09-15
Hi,
   I'm trying to install Ubuntu Server 10.04 in a server which have a 4TB raid array. This is what want my partition table to look like

/boot ext2 200MB
swap       4GB
/     ext4  4TB (wts left from the 4TB array)

But when I try to configure this with the installation CD it fails because the partition size is grater than 2TB. I see this as a common issue creating a file system in a partition > 2TB, never saw a solution for this though. I saw in one pace where the instructions said to modify the kernel config to enable some flags so that 'parted' will support this. This is not an option for since I'm either using a live CD or an installation CD. Is there way that I can make this happen? Thank you in advance...

---

### Post by koenn on 2010-09-15
run ```
parted
``` or ```
gparted
```


edit:
sorry, missed the comments on parted in your OP. Exactly why can't you run it ?

---

### Post by oldfred on 2010-09-15
Not with MBR (msdos), you can use gpt but gpt will not let you boot windows but is fine for Ubuntu.

GPT info 
[http://www.cyberciti.biz/tips/fdisk-unable-to-create-partition-greater-2tb.html](http://www.cyberciti.biz/tips/fdisk-unable-to-create-partition-greater-2tb.html)
[http://www.ibm.com/developerworks/linux/library/l-gpt/](http://www.ibm.com/developerworks/linux/library/l-gpt/)
[http://en.wikipedia.org/wiki/GUID_Partition_Table](http://en.wikipedia.org/wiki/GUID_Partition_Table)
MBR details including 2TiB limit and GPT link
[http://en.wikipedia.org/wiki/Master_boot_record](http://en.wikipedia.org/wiki/Master_boot_record)
[http://en.wikipedia.org/wiki/UEFI](http://en.wikipedia.org/wiki/UEFI)
grub2 & GPT info
[http://grub.enbug.org/BIOS_Boot_Partition](http://grub.enbug.org/BIOS_Boot_Partition)
In a GPT partition map, the 31 kiB area after Master Boot Record where GRUB is usually embedded to, does not exist. When GRUB can't be embedded, its only option is to use blocklists, which are unreliable and discouraged. 

Advantages srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
Multiboot install with gpt & using gdisk
[http://ubuntuforums.org/showthread.php?t=1566090](http://ubuntuforums.org/showthread.php?t=1566090)
This link says they just installed grub2 to the drive and it found the BIOS boot partition.
[http://www.mail-archive.com/grub-devel@gnu.org/msg12109.html](http://www.mail-archive.com/grub-devel@gnu.org/msg12109.html)
Since the BIOS Boot Partition ("bios_grub" flag set in GNU Parted) is used without a filesystem for storing GRUB 2 boot code, and since the EFI System Partition (ESP) is used by EFI with a FAT-32 filesystem for storing EFI files, the two cannot be the same partition.
Converting:
[http://ubuntuforums.org/showthread.php?t=1454252](http://ubuntuforums.org/showthread.php?t=1454252)

---

### Post by shahansudu on 2010-09-15
Thank you koenn and oldfred for the quick reply. So I was not aware that I can change the partition table type from the CD as mentioned in on of the links you provided. I'm going to try some of these things.

My comment on failing to use parted is... I tried booting into a Ubuntu Live CD and from their ran parted to create the partition table and it failed creating a 4TB partition saying Max its beyond the allowed range (or something similar to that). Its entirely possible that I was using the default and did not change the partition table type.

Thanx for the help I think I know little more about this now

---

### Post by oldfred on 2010-09-15
You will need an additional small partition for grub's file. This partition is not used for anything else and often is not seen in any partition listings.

Since the BIOS Boot Partition ("bios_grub" flag set in GNU Parted)

---

### Post by koenn on 2010-09-15
> **shahansudu said:**
> 
My comment on failing to use parted is... I tried booting into a Ubuntu Live CD and from their ran parted to create the partition table and it failed creating a 4TB partition saying Max its beyond the allowed range (or something similar to that). Its entirely possible that I was using the default and did not change the partition table type.

most likely.
I ran into a similar problem once trying to do 4TB partitions with fdisk. That's when i found out you'd need parted and gpt to do that.

---

### Post by shahansudu on 2010-09-15
So for the heck of it I tried installing again without changing anything on partition table type... It worked and I dont know how...

---

### Post by koenn on 2010-09-16
funny. 

how about you run
```

sudo parted
(parted) print

```
and see what partition table type etc you ended up with ... 
(maybe post the output here, I'm curious ...)

---

### Post by guneza on 2010-11-08
Hey!

I just had a similar issue whilst setting up a RAID5 over four 2TB disks. Here's how I solved the problem.

Being used to fdisk, I started parted in interactive mode on the MD device:
```

root@fcnoos-issync:~# parted /dev/md0
GNU Parted 2.2
Using /dev/md0
Welcome to GNU Parted! Type 'help' to view a list of commands.
(parted) p
Model: Unknown (unknown)
Disk /dev/md0: 6001GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start  End  Size  Type  File system  Flags

(parted)

```

As you can see, the partition table is msdos, and thus stopping me from creating a partition > 2TB. Thus, changed it to GPT:

```

(parted) mklabel gpt 
Warning: The existing disk label on /dev/md0 will be destroyed and all data on this disk will be lost. Do you want to continue?
Yes/No? yes

(parted) p
Model: Unknown (unknown)
Disk /dev/md0: 6001GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt

Number  Start  End  Size  Type  File system  Flags

(parted)

```

Then, I created an extended partition with the full RAID size:

```
(parted) mkpart extended 1 6001GB
```

Exited parted, and forced an XFS partition creation:

```
mkfs.xfs -f /dev/md0p1
```

And mounted it to /srv:

```
mount /dev/md0p1 /srv
```

Lots of space, yummy!

```
df -h /srv
Filesystem            Size  Used Avail Use% Mounted on
/dev/md0p1            5.5T  4.3M  5.5T   1% /srv

```

Hope this helps! Cheers!

---

### Post by srs5694 on 2010-11-08
> **guneza said:**
> Then, I created an extended partition with the full RAID size:

```
(parted) mkpart extended 1 6001GB
```

One of the beauties of GPT is that it does away with the ancient hack of extended/logical partitions. It appears that parted, used as you did, assigns the "partition type" code ("extended" in your example) as the partition's label. At least, that's what happened in my test to replicate what you did; my test disk now has a partition that's named "extended:"

```

$ sudo gdisk -l /dev/sdc
GPT fdisk (gdisk) version 0.6.13

Partition table scan:
  MBR: protective
  BSD: not present
  APM: not present
  GPT: present

Found valid GPT with protective MBR; using GPT.
Disk /dev/sdc: 31576064 sectors, 15.1 GiB
Logical sector size: 512 bytes
Disk identifier (GUID): 9414FD3D-865E-4225-8622-C948C001067B
Partition table holds up to 128 entries
First usable sector is 34, last usable sector is 31576030
Partitions will be aligned on 2048-sector boundaries
Total free space is 12046269 sectors (5.7 GiB)

Number  Start (sector)    End (sector)  Size       Code  Name
   1            2048        19531775   9.3 GiB     0700  extended

```

This is perfectly legal and won't cause problems, but you should be aware that the name "extended" is just a name, and it's unrelated to an MBR extended partition. You can change it various ways, if you like:

```

$ sudo gdisk /dev/sdc
GPT fdisk (gdisk) version 0.6.13

Partition table scan:
  MBR: protective
  BSD: not present
  APM: not present
  GPT: present

Found valid GPT with protective MBR; using GPT.

Command (? for help): c
Using 1
Enter name: Freddy

Command (? for help): p
Disk /dev/sdc: 31576064 sectors, 15.1 GiB
Logical sector size: 512 bytes
Disk identifier (GUID): 9414FD3D-865E-4225-8622-C948C001067B
Partition table holds up to 128 entries
First usable sector is 34, last usable sector is 31576030
Partitions will be aligned on 2048-sector boundaries
Total free space is 12046269 sectors (5.7 GiB)

Number  Start (sector)    End (sector)  Size       Code  Name
   1            2048        19531775   9.3 GiB     0700  Freddy

```

...or with parted:

```

$ sudo parted /dev/sdc
GNU Parted 2.3
Using /dev/sdc
Welcome to GNU Parted! Type 'help' to view a list of commands.
(parted) name 1 Nemo                                                      
(parted) print                                                            
Model:  USB_DRIVE (scsi)
Disk /dev/sdc: 16.2GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt

Number  Start   End     Size    File system  Name  Flags
 1      1049kB  10.0GB  9999MB  ext4         Nemo

```

---

### Post by guneza on 2010-11-08
Thank you for the very good explanation. :)

I have now changed the name of the disk from 'extended' to 'syncdisk':
```

root@fcnoos-issync:/var/log# gdisk -l /dev/md0
GPT fdisk (gdisk) version 0.5.1

Partition table scan:
  MBR: protective
  BSD: not present
  APM: not present
  GPT: present

Found valid GPT with protective MBR; using GPT.
Disk /dev/md0: 11721086976 sectors, 5.5 TiB
Disk identifier (GUID): 00BC6B44-DF27-4991-8261-B67DDB75DD07
Partition table holds up to 128 entries
First usable sector is 34, last usable sector is 3131152350
Total free space is 701 sectors (350.5 KiB)

Number  Start (sector)    End (sector)  Size       Code  Name
   1             384      3131151999   5.5 TiB     0700  extended
root@fcnoos-issync:/var/log# gdisk /dev/md0
GPT fdisk (gdisk) version 0.5.1

Partition table scan:
  MBR: protective
  BSD: not present
  APM: not present
  GPT: present

Found valid GPT with protective MBR; using GPT.

Command (? for help): c
Using 1
Enter name: syncdisk

Command (? for help): p
Disk /dev/md0: 11721086976 sectors, 5.5 TiB
Disk identifier (GUID): 00BC6B44-DF27-4991-8261-B67DDB75DD07
Partition table holds up to 128 entries
First usable sector is 34, last usable sector is 3131152350
Total free space is 701 sectors (350.5 KiB)

Number  Start (sector)    End (sector)  Size       Code  Name
   1             384      3131151999   5.5 TiB     0700  syncdisk

Command (? for help): q
root@fcnoos-issync:/var/log# 

```

Cheers!

---

