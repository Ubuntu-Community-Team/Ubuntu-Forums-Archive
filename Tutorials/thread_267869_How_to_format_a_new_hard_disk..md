---
title: "How to format a new hard disk."
date: 2006-09-29
forum: Tutorials
---

### Post by Bigglez on 2006-09-29
_**How to "format" a new hard disk.**_
So, you have been visited by the gigabyte fairy and you have a brand new external USB hard drive, you might be irked to find that it's already formatted with the NTFS filesystem because it's a default world out there ...
What to do?

(This will work for any old hard drive, so even if you have an internal one - you're good )

_**Stuff I assume**_
Your drive needs to be plugged-in and your system must see it. You should see an icon appear on your desktop. If not then open a console and try this:
If you have an external USB drive:
```
cd /dev
ls s*
```
If you have an internal drive:
```
cd /dev
ls hd*
```
You should see a list of things something like this for example:
```
sda  sda1  sdb  sdb1
```
That shows you that your system knows about two physical external drives (sda and sdb) as well as the partition that is on each. So, now you know that your machine knows about your new drive(s).

Make sure that your new drive is not mounted. Let's assume it's name is sda1 (please substitute your own details), at the console type:
```
mount | grep sda1
``` If you see any results then it's mounted, so do this:```
umount -l /dev/sda1
```

_**Warning**_
Please ***ensure*** that you know ***exactly*** which drive you are going to erase and format... I speak from experience, hoo-boy! So, make sure you know which name identifies your drive. hdb or sda or sdc or whatever. Be sure. If you are not sure, then use whatever built-in tools that your distro has to try and get yourself oriented. You can also do this at the console:```
fdisk -l
``` Now look at all the drives carefully, look at their types and sizes and make your mind up.

_**GUIs and Consoles**_
I use Kubuntu 6.06. I quite frankly could not figure out how to prepare my new USB drive from any of the system control panels. It was too confusing and ambigous. I don't know (and can only hope) whether Ubuntu is any better. The upshot? I will use the command line!

_**Let's get going!**_
**Removing and creating a partition**
Having decided your drive's name (let's call it sda) we must now remove the default partition that the manafacturer put there:
```
sudo fdisk /dev/sda
```
This will start fdisk. We want to remove the partion(s), there should only be one.
Press d <enter>(for delete).
It might ask you for the partition number, press 1 and enter. If there are more then delete them too.

Now to make a new partition.
Press n <enter> (for new), then p <enter> (for primary), then 1 <enter> and then simply press enter for the next two questions.
This will make a new partition that uses the entire disk. If you want more complex partitioning then read the fdisk manual (man fdisk) or use parted or some other app.
Here's what we did with n, the values will differ from yours:
```

Command (m for help): n                                                      
Command action                                                               
   e   extended                                                              
   p   primary partition (1-4)                                               
p                                                                            
Partition number (1-4): 1                                                    
First cylinder (197-621, default 197):                               
Using default value 197                                                      
Last cylinder or +size or +sizeM or +sizeK (197-621, default 621): +128M

```

Now to write the new partion and exit, press w and enter.
You should be ready to make a filesystem now.

**Making a filesystem : "Formatting" **
You need to put a system in-place, on the disk, such that it can handle files. This is called (unsurprisingly) a filesystem.
The one we are going to use is called "ext3". On Gnu/Linux we are spoiled for choice and there are loads of filesystems you can use, go do some research if you want to.
So, let's make the filesystem:```
sudo mkfs.ext3 /dev/sda1
```
* Note the **1** at the end, because we are making the filesystem in that partition (thanks Mike)

Now it will go off and do strange stuff, simply wait for it to finish.

_**Using the new file system**_
Well, at this point you should be able to right-click on the icon (on your Desktop) and choose "mount" (I assume that's the verb it will present to you). After that you should be able to open a window and use the drive*
* all this assumes it's an external USB drive.
If you cannot then you will need to mount it yourself, try:```

sudo mkdir /media/sda1
sudo mount /dev/sda1 /media/sda1
```
Note: We are actually mounting the first partition on the drive, hence the 1 at the end: sda1
And the mounted directory can be anywhere you like, but its common location is /media.

If those two steps worked then you are 90% done.

You may need to make a single folder in the new drive and give it your user permissions:
```
cd /media/sda1
sudo mkdir afolder
chown you:you afolder
```
Where you insert your username and desired folder name as appropriate.

Please search around on the subject of your fstab and getting the drive to mount automatically when you reboot. There are plenty of howto's out there on that subject. I must post and run now.

HTH

Keywords for searching:
format filesystem ext ext2 ext3 NTFS linux make new external internal USB drive disk partition

---

### Post by MikeBenza on 2006-10-08
I think you intend to mkfs.ext3 the partition, not the whole device, hence:
```
sudo mkfs.ext3 /dev/sda1
```

Also, you need to specify a mount point for the device, since it's new, it won't be in fstab, so this:

```
sudo mount /dev/sda1
```

Should be this:

```

sudo mkdir /where/you/want/this/drive/to/be/mounted
sudo mount /dev/sda1 /where/you/want/this/drive/to/be/mounted

```

- Mike

---

### Post by Bigglez on 2007-01-15
When it comes to external USB drives I have since found it best **not to create** any mount points (i.e. folders in /media) for the devices. This is because it gets done automagically by Ubuntu. 

If you run into trouble and it cannot mount things, then look into making your own mountpoints.


/d

---

### Post by Dabrorius on 2007-11-01
hi I'm trying to make new virutal hd work in vmware (ubuntu under windows host)
i add new HD boot system and follow this tutorial and everything is ok until I get to part when I type in command

> sudo mkfs.ext3 /dev/sdb1

 i get this error

> 
mke2fs 1.40.2 (12-Jul-2007)
mkfs.ext3: inode_size (128) * inodes_count (0) too big for a
        filesystem with 0 blocks, specify higher inode_ratio (-i)
        or lower inode count (-N). 

anyone know what the problem might be

---

### Post by gamont on 2008-05-09
ok

---

### Post by MadKAT on 2008-05-10
This has been very handy! Thanks a bunch! Worked well with my new USB drive :)

---

### Post by sml on 2008-12-31
Can't we just use GParted?

For a new SATA hard disk, GParted must be the easiest option surely. Does it not work for a USB drive?

---

### Post by Kaptnik on 2009-06-25
> **Dabrorius said:**
> hi I'm trying to make new virutal hd work in vmware (ubuntu under windows host)
i add new HD boot system and follow this tutorial and everything is ok until I get to part when I type in command



 i get this error



anyone know what the problem might be

After you ran sudo fdisk /dev/sdb1 , and deleted the existing partitions by hitting the d key and creating a new one by hitting n, did you choose 'p' (primary) or 'e' (extended).

If you chose 'e', re-run the command and choose 'p' instead. That should solve your problem.

---

### Post by JCyberinux on 2010-11-20
geee.. thanks for this one... finding solution for formatting my new hard disk.

---

### Post by tlroche on 2010-12-02
> **sml said:**
> For a new SATA hard disk, GParted must be the easiest option surely. Does it not work for a USB drive?

It does: I just repartitioned and reformatted an external USB SATA (Samsung HM641JI) using gparted, and all seems well.

---

### Post by ralbach on 2011-01-02
Hi Folks,

I've spent a large amount of time (@10 hours over two days) trying to format a used 80G IDE HDD. I've read a good number of these threads.

Things I have done:

Used 10.10's Disk Utility, GParted, fdisk, cfdisk.

The general issue seems to be that in every instance the partition table is not recognized. As an example cfdisk always opens with a statement that the partition table is not there and efforts in the disk utility and partition utilities from the CD tell me that all NEW efforts will not work as I must first create the partition table.

Now in cfdisk I get a similar partition table message on start up but it will happily allow me to create NEW and PRINT the table on demand. Once I exit however (after WRITE) the others or another running of cfdisk repeats the missing partition table.

Now just for grins I booted off an old Win98 3.5 floppy and ran fdisk. It created its partition and ran a verification.

After that I repeated another few hours w Ubuntu and its tools. Same issues repeated.

Any general thoughts?

Thanks,

-Robert

---

### Post by qneill on 2011-01-06
> **ralbach said:**
> Hi Folks,

I've spent a large amount of time (@10 hours over two days) trying to format a used 80G IDE HDD. I've read a good number of these threads.
...
 Once I exit however (after WRITE) the others or another running of cfdisk repeats the missing partition table.
...
Any general thoughts?

Thanks,

-Robert
Are you running as root?

Any messages from the kernel? (use "dmesg | tail")

Try using "hdparm -I ..." to talk to the drive (type "man hdparm" to learn more)

Try plain fdisk instead of cfdisk (you probably already tried that).

Final thought: if you are *formatting* an 80G drive it must be empty/unused... perhaps you should consider upgrading to a drive that just works [http://www.pricewatch.com/hard_removable_drives/](http://www.pricewatch.com/hard_removable_drives/).

If you need IDE, try your local computer store, I bet they will give you bag of IDE drives to get it off their desk.
-- 
Quentin

---

### Post by Shakey Hands on 2012-06-19
thx!

---

### Post by oldfred on 2012-06-20
Thread closed.

Information has not been updated, please start new thread with questions.

---

