---
title: "Add new HDD for Samba only"
date: 2010-02-04
forum: Server Platforms
---

### Post by HighCommander540 on 2010-02-04
Hello, everyone. I recently got myself a new hard drive and I want to use it as my Samba share. I just want the hard drive itself to store the files.

I know once I get it set up it should be easy to tell Samba that's where I want it to store and look for files.

Problem is I need to make it so the computer can use the hard drive first. I have already installed the drive. I just don't know how to get Ubuntu to recognize the drive.

I also need to create a partition that uses the whole drive and format it to ext3, then I need to mount it somewhere for Samba to use.

This would be easy to do with Ubuntu desktop, but I am using Ubuntu server and I don't know how to do it. I have read that I will need to use fdisk, but the post wasn't to clear on what to do.

There are also setting for the partition and stuff like that...What do I need to do to get this up and running?

---

### Post by capscrew on 2010-02-04
> **HighCommander540 said:**
> Hello, everyone. I recently got myself a new hard drive and I want to use it as my Samba share. I just want the hard drive itself to store the files.

I know once I get it set up it should be easy to tell Samba that's where I want it to store and look for files.

Problem is I need to make it so the computer can use the hard drive first. I have already installed the drive. I just don't know how to get Ubuntu to recognize the drive.

I also need to create a partition that uses the whole drive and format it to ext3, then I need to mount it somewhere for Samba to use.

This would be easy to do with Ubuntu desktop, but I am using Ubuntu server and I don't know how to do it. I have read that I will need to use fdisk, but the post wasn't to clear on what to do.

There are also setting for the partition and stuff like that...What do I need to do to get this up and running?

You can use fdisk to create the 1 partition on the drive.  From memory:```
fdisk /dev/sdb
``` Check the man pages for the specific syntax.

After you have created the partition with fdisk you need to create the filesystem on the partition.  From the command line you can use *mkfs.ext3* to create the file system on that partition.  See [**_[COLOR="Navy"]here [/COLOR]_**]("http://linux.die.net/man/8/mkfs.ext3")for info.

When this is completed I would find the UUID of the partition ```
sudo blkid
```
At this point you need a mount point.  I created a generic mount point called */smb* using ```
sudo mkdir /smb
```  Now you can mount the partition using the *mount *command.  If that works then you can add the partition to the */etc/fstab *file using the UUID to automount it when booting up.

if this is unclear let me know and we can drill down together.

---

### Post by trundlenut on 2010-02-04
I did this pretty much as Capscrew suggests, it wasn't hard.

---

