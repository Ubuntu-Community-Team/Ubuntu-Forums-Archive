---
title: "Trying to Fail a software raid array and rebuild it."
date: 2011-02-26
forum: Server Platforms
---

### Post by derr12 on 2011-02-26
Using a fresh copy of server 10.04

Hi there, im trying to simulate a failed raid array on a pair of 2tb disks.  

Here is the procedure i have been following so far:

- Remove the dead disk partitions from each of the raid 1 arrays (substitute the correct md devices and partitions)
- mdadm /dev/md0 -r /dev/sdb2
- mdadm /dev/md1 -r /dev/sdb3

- remove the old disk
- insert the new disk

- copy the partition table from the good disk to the new one (again substituting the correct devices). Note that you are specifying the full drives (sda and sdb) not individual partitions on those drives (sda2 or sdb3)

- sfdisk -d /dev/sda | sfdisk /dev/sdb

I get an error here that sfdisk does not support gpt (guid partition table).   I thought sfdisk did support gpt?  It says to use parted, but i cant find a command that copies a partition table over from another disk in parted documentation.  

Any suggestions?  I suppose i could make the partitions manually, but im writing a procedure for people who arent that technical and i need it to be simple enough to be run in my absence. manually building the partitions would be too hard for them.

---

### Post by srs5694 on 2011-02-26
> **derr12 said:**
> - copy the partition table from the good disk to the new one (again substituting the correct devices). Note that you are specifying the full drives (sda and sdb) not individual partitions on those drives (sda2 or sdb3)

- sfdisk -d /dev/sda | sfdisk /dev/sdb

I get an error here that sfdisk does not support gpt (guid partition table).   I thought sfdisk did support gpt?

No, it doesn't. The fdisk, sfdisk, and cfdisk tools work on Master Boot Record (MBR) disks. At least some of them work on some other disk types, too, like BSD disklabels. They do *not* support GUID Partition Table (GPT) disks.

> It says to use parted, but i cant find a command that copies a partition table over from another disk in parted documentation. 

It might be possible to create a script that would do the job; however, there is a simpler solution....

You can use my gdisk or sgdisk (part of the [GPT fdisk](http://www.rodsbooks.com/gdisk/) package), available from [its Sourceforge page:](http://sourceforge.net/projects/gptfdisk/files/)

```

sudo sgdisk --replicate=/dev/sdb /dev/sda
sudo sgdisk --randomize-guids --move-second-header /dev/sdb

```

The "--randomize-guids" option is necessary for your case, since you're planning to use both disks in a single computer; you might not want to use it if you were creating an exact disk copy as a backup disk. The "--move-second-header" option is not necessary if the two disks are *exactly* the same size. Note that two disks advertized as being of the same size may differ by a small amount. Thus, unless you're using disks with the same model number, it's best to use "--move-second-header". Also, in running my tests to verify these commands, I found that the copy procedure only works if the target disk is as large as or larger than the source disk. (I've just added that limitation as a bug to my to-do list, so I'll fix it for the next release, which I'm hoping to make this weekend.)

The same thing can be done in gdisk by using the "u" option on the experts' menu, then launching gdisk on the target disk and using the "e" option on the experts' menu (to move the second header, if necessary), the "g" option on the experts' menu (to change the disk's GUID), and the "c" option on the experts menu on each partition (to change the partitions' GUIDs). This is obviously much more tedious than using sgdisk, but it is possible.

---

### Post by derr12 on 2011-02-26
Thats done the trick.  rebuilding the array right now!

---

