---
title: "Ubuntu - Expand storage"
date: 2020-06-15
forum: Server Platforms
---

### Post by perpetualwar6 on 2020-06-15
Hey all,

First time posting - I'm a noob when it comes to Ubuntu however moving some servers to Ubuntu for my work has been fantastic. I've ran into an issue - We are migrating all of our servers to AWS. In the process, I am moving over Owncloud that runs off Ubuntu 18.04 LTS. Unfortunately, I do not have Admin privileges on AWS so I don't know how the VM was set up. I requested an Ubuntu server with 2.5 TB allocated to it. Upon logging in, it only said there was less than 8 GB on the server. I can see that there is an unmounted disk in my setup that is 2.5 TB large. My issue is that I do not know how to mount and integrate into my existing 8 GB OS. 

**Here is my unmounted disk:**
*Disk /dev/nvme0n1: 2.5 TiB, 2684354560000 bytes, 5242880000 sectors*
*Units: sectors of 1 * 512 = 512 bytes*
*Sector size (logical/physical): 512 bytes / 512 bytes*
*I/O size (minimum/optimal): 512 bytes / 512 bytes*
*Disklabel type: gpt*
*Disk identifier: F9ACD6DC-6962-46C4-AC34-4438EBA73E3F*

**Here is the mounted disk I'm running on:**
*Disk /dev/nvme1n1: 8 GiB, 8589934592 bytes, 16777216 sectors*
*Units: sectors of 1 * 512 = 512 bytes*
*Sector size (logical/physical): 512 bytes / 512 bytes*
*I/O size (minimum/optimal): 512 bytes / 512 bytes*
*Disklabel type: dos*
*Disk identifier: 0xfe3a9f65*

*Device         Boot Start      End  Sectors Size Id Type*
*/dev/nvme1n1p1 *     2048 16777182 16775135   8G 83 Linux*


**Here is my current setup:**
*NAME        MAJ:MIN RM  SIZE RO TYPE MOUNTPOINT*
*loop0         7:0    0   18M  1 loop /snap/amazon-ssm-agent/1566*
*loop1         7:1    0 93.9M  1 loop /snap/core/9066*
*loop3         7:3    0   97M  1 loop /snap/core/9289*
*nvme0n1     259:0    0  2.5T  0 disk*
*nvme1n1     259:1    0    8G  0 disk*
*&#9492;&#9472;nvme1n1p1 259:2    0    8G  0 part /*

As you can see, I am running on the nvme1n1 disk. The nvme1n1 disk label is set as DOS.
nvme0n1 disklabel is GPT.

How do I merge nvme0n1 with nvme1n1 or just create an additional partition on nvme1n1 and add nvme0n1 into it? I have an idea of how to do it but Google sends me further and further down the rabbit hole where I've just become confused on how to do this. I apologize for any misuse of terms - Any help would be greatly appreciated. Thanks all!

---

### Post by darkod on 2020-06-15
There is not really an easy way to merge this when it wasn't done at the beginning.

I suggest to speak to an admin which can recreate the AWS instance because this is new empty instance and it will be faster redoing it than being stuck with "wrong" server later...

The person creating the instance has to know how much space to assign to what. For example, if you need one big space then they need to create the instance like that.

On the other hand if 8GB is enough for the root and you need 2.5TB for another mount point (like /home, or /srv, or /data, etc), then it is always best to do that setup during instance creation.

---

### Post by perpetualwar6 on 2020-06-15
> **darkod said:**
> There is not really an easy way to merge this when it wasn't done at the beginning.

I suggest to speak to an admin which can recreate the AWS instance because this is new empty instance and it will be faster redoing it than being stuck with "wrong" server later...

The person creating the instance has to know how much space to assign to what. For example, if you need one big space then they need to create the instance like that.

On the other hand if 8GB is enough for the root and you need 2.5TB for another mount point (like /home, or /srv, or /data, etc), then it is always best to do that setup during instance creation.
Hi darkod, thanks for the info. Unfortunately, this server is already live with Owncloud installed. It wasn't my call to make the server live - With that said, what options do I have if recreating the AWS instance is not an option?

---

### Post by darkod on 2020-06-15
Depending where you have (or plan to have) most of your data?

Is it inside existing folder or you can use new folder created for this purpose?

For example, by default there is no folder named 'data' inside the root. So if you create /data you can create one big partition in /dev/nvme0n1 and mount that partition on /data.

From there onwards, any application that needs to store large data will need to be configured to use folder inside the /data path. That way it will not use space from the 8GB, it will use space from the 2.5TB.

If you need to move one of the existing system folders it will be more complicated than the above.

---

### Post by perpetualwar6 on 2020-06-15
Since Owncloud is a file share, I've created a folder where all the data is saved:

/home/ubuntu/owncloud/data

This resides on the /dev/nvme1n1p1 partition

---

### Post by LHammonds on 2020-06-16
A perfect example of how LVM would save the day.  Sorry I don't know how else to unstick you from this situation since I exclusively work with LVM partitions to avoid this kind of mess.  Is there any chance you can spin up another AWS, set it up correctly and migrate it over so you are not stuck with this?

I would setup [Ubuntu Server 20.04 LTS](https://hammondslegacy.com/forum/viewtopic.php?f=40&t=273) using LVM.   Instead of ownCloud, I would recommend [NextCloud](https://hammondslegacy.com/forum/viewtopic.php?f=40&t=282) (for similar reasons why I recommend [MariaDB](https://hammondslegacy.com/forum/viewtopic.php?f=40&t=279) over MySQL).

If you are unfamiliar with LVM, here is a tutorial I wrote on the steps necessary to setup 20.04 with LVM and how to go about setting up the initial partition layout...designed for growth to dynamically apply space where needed.

LHammonds

---

### Post by TheFu on 2020-06-16
+1 for fixing this now.  it won't get better and is likely to get much, much worse.

8G really isn't enough for a server.  25G is the safe size.  For data, either use LVM or ZFS and please, please, do not allocate all the storage now.  Leave room to make your backups easier because you can use snapshots (both LVM and ZFS support those).  For the OS, i really don't care if you use LVM or not.  it can make life easier when/if you need to add more storage somewhere - perhaps where the DBMS sits.

I’ve been running nextcloud a few years. We don't really use it for everything but it does have about 20 TB of files stored - most are only read-only NFS mounts because i don't trust the security of php webapps.  Only have about 20 users. Most don't use it.

For data management, LVM and ZFS are about the same, but LVM doesn't have any file system. That gets added as you choose.  ZFS is both a volume manager AND a file system and has some very advanced capabilities.  Both change the ways we think about storage from fixed allocations to allocate what you need, no more, as you need it.  Expanding storage is trivial.  Start w/ 50G for the owncloud data. Hopefully, you put that somewhere outside /var/.  i use /opt/nc-data/  The DBMS goes in the normal place under /var/.

Please consider how you will get backups off-site now, not later.  ZFS has a zsend command that can replicate snapshots between different systems - sorta a fancy block-level replication facility.   [https://github.com/jimsalterjrs/sanoid](https://github.com/jimsalterjrs/sanoid) for your consideration.

But this is your show, not ours.  if you are in over your head - buy an admin book with the steps you need laid out.  Those book can be a self-contained reference for many needed tasks.  Getting quality information in an organized way that doesn't forget the ground-floor skills in the beginning is extremely important.  One of those ubuntu 18.04 500-750pg books.  To be a power-user, [http://linuxcommand.org/tlcl.php](http://linuxcommand.org/tlcl.php) is fine, but not admin-centric.

BTW, whenever posting terminal commands or output, please use _code tags_ so the columns line up. Some output is too hard to read otherwise.

nvme0n1 doesn't have a partition table, no partitions, no PVs, VGs, LVs or any file systems.

i use LVM + snapshots + rdiff-backup for my backups.  Restoring the OS takes 30-45min. Data takes however long the data takes.  My spinning rust storage usually gets about 180 MB/s xfers. About 5 hrs every 4TB.  These backup methods only transmit change data since the last backup, so just a few minutes are needed daily.

---

### Post by perpetualwar6 on 2020-06-16
Thank you The_Fu  & LHammonds - Unfortunately, I'm put in an odd place at the company - I am a Systems Admin and as we migrate to AWS, our CIO is purposely not giving any access to AWS to the Systems Admins within the company which is insanely frustrating. Restarting from step one is not an option.

As for LVM, I think that would be my best bet as I ran into a similar issue in the past resizing our Owncloud instance running at our data center - An IT manager within the company was able to fix the issue using LVM. Now, I've been doing some light reading before I even saw these posts - I have an issue where lvmdiskscan does not return any disks. It returns back as 0 disks, 7 partitions. I created a partition on the unused space (nvme0n1) and because both have file systems, is that the reason why it returns back as 0 disks?

---

### Post by TheFu on 2020-06-16
if an admin doesn't have admin, you need to find a new job.  They have other plans and that doesn't include your employment.

if the complaint is that you can't control AWS settings, that is a completely different issue and doesn't mean they plan to fire you. 
I&#8217;ve never used lvmdiskscan; always used **vgchange -ay**.  if you don't have any LVM objects created (pv, vg, lv s) - there's nothing to find.  Find a reputable tutorial on LVM and play with it inside a local VM to see how things work.  Above, i provided a list of necessary objects that have to be created, in order.  You need a partition table first.

Why would there be 7 partitions?  That's just wrong and would defeat the purpose for using LVM.  There are lots of LVM posts in these forums with layout examples.

---

### Post by perpetualwar6 on 2020-06-16
Thanks TheFu. Will do so. Cheers

---

### Post by LHammonds on 2020-06-16
> **perpetualwar6 said:**
> I have an issue where lvmdiskscan does not return any disks
That utility looks for "existing" LVM partitions...which you do not have...thus nothing found...which is why I suggested the use of LVM because I did not see any disks using it either.  When you format a disk with fdisk, you would use option 8e which sets it up as a "Linux LVM"

For detailed steps, look at the "Adding More Hard Disks" section talking about LVM management on [this page](https://hammondslegacy.com/forum/viewtopic.php?p=814#p814).

LHammonds

---

### Post by perpetualwar6 on 2020-06-17
> **LHammonds said:**
> That utility looks for "existing" LVM partitions...which you do not have...thus nothing found...which is why I suggested the use of LVM because I did not see any disks using it either.  When you format a disk with fdisk, you would use option 8e which sets it up as a "Linux LVM"

For detailed steps, look at the "Adding More Hard Disks" section talking about LVM management on [this page]("https://hammondslegacy.com/forum/viewtopic.php?p=814#p814").

LHammonds About to read now - Thank you, @LHammonds

---

### Post by LHammonds on 2020-06-17
> **perpetualwar6 said:**
> About to read now - Thank you, @LHammonds
Just for absolute clarification, those instructions are for a system with LVM already in use which is NOT your server.

**EDIT:** Yes, it is possible to add LVM to storage you mount but I just wanted to be clear that the article I linked explains LVM steps/usage for a specific scenario (such as setting up a server from scratch) rather than as steps for solving this specific situation...which I already explained that I am of no help. ;)

LHammonds

---

### Post by TheFu on 2020-06-17
> **LHammonds said:**
> Just for absolute clarification, those instructions are for a system with LVM already in use which is NOT your server.

LHammonds

A good way to think about LVM is that an LV (logical volume) can be created for critical directories and mounted exactly where needed with the needed amount of storage for the next 6-12 months.

I do virtual machines, so each gets an LV.  If more storage is needed, I'll add another virtual disk, add that disk to the existing VG, then just expand the LV. Takes 20-30 seconds and storage doesn't get wasted being pre-allocated to locations that just don't need it.  An LV can usually be thought of as a normal disk partition, just with extra flexibility including the ability to change it while the system keeps running.  Just a last week (perhaps the week before), I showed exactly, step-by-step, how to add more storage to an existing LV inside a VM, in these forums.
```
$ sudo pvs
  PV         VG            Fmt  Attr PSize   PFree
  /dev/vda5  vgubuntu-mate lvm2 a--  <29.50g    0 
  /dev/vdb1  vgubuntu-mate lvm2 a--  <10.00g 6.39g

$ sudo lvs
  LV     VG            Attr       LSize   ....
  home   vgubuntu-mate -wi-ao---- 12.00g
  root   vgubuntu-mate -wi-ao---- 17.00g
  swap_1 vgubuntu-mate -wi-ao----  4.10g

$ lsblk -e 7 -o name,size,type,fstype,mountpoint
NAME                       SIZE TYPE FSTYPE      MOUNTPOINT
vda                         30G disk             
&#9500;&#9472;vda1                     512M part vfat        /boot/efi
&#9500;&#9472;vda2                       1K part             
&#9492;&#9472;vda5                    29.5G part LVM2_member 
  &#9500;&#9472;vgubuntu--mate-root     17G lvm  ext4        /
  &#9500;&#9472;vgubuntu--mate-swap_1  4.1G lvm  swap        [SWAP]
  &#9492;&#9472;vgubuntu--mate-home     12G lvm  ext4        /home
vdb                         10G disk             
&#9492;&#9472;vdb1                      10G part LVM2_member 
  &#9492;&#9472;vgubuntu--mate-root     17G lvm  ext4        /
```

2 "virtual disks" merged via LVM to expand /. Because that storage is actually from the same SSD, redundancy wasn't a consideration. That could have been for /home or some other LV. All of this was performed as the system kept running.  If I needed to resize vda5, then that would have required downtime.  Partition changes require downtime. LV changes don't, unless shrinking is needed.  Growing LVs is easy. Shrinking is not, which is why allocating just what you need is a core "best practice" for most storage volume management.

So, what does all this mean?  Create an LV for the DBMS directory. Create a different LV for the owncloud data location. Create other LVs for other important groups of directories.  Flexibility is why we use LVM. You don't need to know all the things that flexibility provides today, but if you use tab completion, you'll be able to see the related commands:
pv{tab}
vg{tab}
lv{tab}
see the commands? Note the pvmove, lvchange, pvchange and lvextend commands. Those are what I use mostly. Every once in a while I'll use vgcreate and lvcreate, but lvextend gets used 10x more often than anything else.  Well, that isn't really correct. Every night my backup scripts use lvcreate to make snapshots and lvremove after the backups finish, but I don't type those. They are scripted.

---

