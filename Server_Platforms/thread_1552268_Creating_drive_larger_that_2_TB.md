---
title: "Creating drive larger that 2 TB"
date: 2010-08-13
forum: Server Platforms
---

### Post by dtd646 on 2010-08-13
I have been trying to create a partition larger than 2 TB on my ubuntu 10.04 server.  I have tried multiple files systems, ext4, xfs, etc.  Many of them say that this is totally doable BUT I can't seem to get it working.  I am using the following command when making a xfs partition:
 
mkfs.xfs -f /dev/sda1
 
After the file system is laid down, I check df -h and it lists 2 TB for /dev/sda1.
 
The full partition size listed under fdisk -l is 14 TB, which is what I would like to use for my partition.
 
Any help would be greatly appreciated!

---

### Post by oldfred on 2010-08-13
I am no expert on this but MBR (msdos) has a 2Tib limit. This is why many are converting to gpt. Mac's and some windows servers use gpt. I converted one 160GB drive to gpt just to see if it works and it does, but they are making further improvements in Maverick.

GPT info 
[http://www.cyberciti.biz/tips/fdisk-unable-to-create-partition-greater-2tb.html](http://www.cyberciti.biz/tips/fdisk-unable-to-create-partition-greater-2tb.html)
[http://www.ibm.com/developerworks/linux/library/l-gpt/](http://www.ibm.com/developerworks/linux/library/l-gpt/)
[http://en.wikipedia.org/wiki/GUID_Partition_Table](http://en.wikipedia.org/wiki/GUID_Partition_Table)
MBR details including 2TiB limit and GPT link
[http://en.wikipedia.org/wiki/Master_boot_record](http://en.wikipedia.org/wiki/Master_boot_record)
[http://grub.enbug.org/BIOS_Boot_Partition](http://grub.enbug.org/BIOS_Boot_Partition)
[http://kubuntuforums.net/forums/index.php?topic=3106368.0](http://kubuntuforums.net/forums/index.php?topic=3106368.0)

GPT fdisk Tutorial -srs5694 in forums
[http://ubuntuforums.org/showthread.php?t=1439794](http://ubuntuforums.org/showthread.php?t=1439794)
[http://www.rodsbooks.com/gdisk/](http://www.rodsbooks.com/gdisk/)

---

### Post by dtd646 on 2010-08-13
Thanks for the quick reply.  I will research converting to a gpt drive.  If you know a quick and dirty way to do it on Ubuntu, it would be appreciated.

---

### Post by CharlesA on 2010-08-13
If you want to create a partition bigger then 2TB, you need a GPT (GUID Partition Table) partition. I needed to create a GPT when I created by 4TB RAID-5 array. You can use gparted to do so and I suggest using it, since I'm not sure how easier it is to create a GPT from the command line.

---

### Post by koenn on 2010-08-13
> **CharlesA said:**
> If you want to create a partition bigger then 2TB, you need a GPT (GUID Partition Table) partition. I needed to create a GPT when I created by 4TB RAID-5 array. You can use gparted to do so and I suggest using it, since I'm not sure how easier it is to create a GPT from the command line.


fairly easy
```

k@ft:~$ sudo parted
GNU Parted 2.2
Using /dev/sda
Welcome to GNU Parted! Type 'help' to view a list of commands.
(parted) 

```

---

### Post by CharlesA on 2010-08-14
> **koenn said:**
> fairly easy
```

k@ft:~$ sudo parted
GNU Parted 2.2
Using /dev/sda
Welcome to GNU Parted! Type 'help' to view a list of commands.
(parted) 

```
Nice!

Thanks for the info!

---

