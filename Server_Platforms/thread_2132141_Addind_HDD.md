---
title: "Addind HDD"
date: 2013-04-03
forum: Server Platforms
---

### Post by lakz on 2013-04-03
Hi,
I have Ubuntu Server 12.04.2 LTS installed on my ESXI host. I attached 2 RDM to it (4TB and 3TB). I'm willing to create a FlexRAID array with it.

> Disk /dev/sdb: 4000.8 GB, 4000787030016 bytes255 heads, 63 sectors/track, 486401 cylinders, total 7814037168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x00000000


   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1  4294967295  2147483647+  ee  GPT
**Partition 1 does not start on physical sector boundary.**


WARNING: GPT (GUID Partition Table) detected on '/dev/sdc'! The util fdisk doesn't support GPT. Use GNU Parted.




Disk /dev/sdc: 3000.6 GB, 3000592982016 bytes
255 heads, 63 sectors/track, 364801 cylinders, total 5860533168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x00000000




I spend two hours trying to figure out how to add new HDDs to Ubuntu. I tried different guides but they're either outdated or completely overwhelming (it's my first time using Linux).

Is there an up-to-date idiot proof way to go about it?




ps: I have the lastest version of webmin installed.

---

### Post by spynappels on 2013-04-04
Hi there,

If this is a virtual machine on an ESXi host, you will need to add the disks as block storage devices (datastores) in ESXi first, then create 2 new virtual hard drives (vmdk files) on these new datastores and add these to the VM.
After this you can go through the normal Linux setup for adding new disks. As a rough guide, this will include:

[LIST=1]
[*]Creating new partition(s) on each new disk. (Check out Gparted)
[*]Creating a filesystem on each partition
[*]Editing fstab to mount each filesystem at boot
[/LIST]

But these steps will only work after doing the ESXi steps first.

---

### Post by darkod on 2013-04-04
Is what you posted from ubuntu or the esxi host?

If it's from ubuntu, it's not really a good practice to start partition on sector 1. If working in MiB, you should leave 1MiB unallocated at front.
If working in sectors that are 512B like in your case, that would mean 2048 sectors, that would be the start point of the first partition.

On top of that, on gpt disks ubuntu needs a small 1MiB partition with NO filesystem and the bios_grub flag set, so that it can install grub2 properly to the disk.

And try using the command line and parted for the disk partitioning, webmin can be real pain. In fact, I would stay away from it, as much as having a GUI tool looks appealing. It often touches the config files in a different, specific way.

Partitioning in the command line is very easy, no matter the setup you want to achieve. If you have an idea what you want to do, we can help with specific commands in the command line.

I'm not familiar with FlexRAID myself. Is that like software raid, like mdadm?

---

### Post by lakz on 2013-04-04
> **spynappels said:**
> 
If this is a virtual machine on an ESXi host, you will need to add the disks as block storage devices (datastores) in ESXi first, then create 2 new virtual hard drives (vmdk files) on these new datastores and add these to the VM.

Yes, it is a VM on the ESXi host. I didn't want to be all over the place by giving too much details in my initial post, I apologize for that. I'm quite familiar with ESXi. My HDDs are physically mapped to the VM using [this trick]("http://www.tumfatig.net/20120226/raw-device-mapping-of-local-sata-disks"). As you can see in the OP, the disks are successfully attached to the VM and recognized in Ubuntu.

> **spynappels said:**
> 
After this you can go through the normal Linux setup for adding new disks. As a rough guide, this will include:


[LIST=1]
[*]Creating new partition(s) on each new disk. (Check out Gparted)
[*]Creating a filesystem on each partition
[*]Editing fstab to mount each filesystem at boot
[/LIST]


The problem lies in this part. I've been using Windows Home Server for years, Linux is foreign to me and so far I failed to understand the basics. I'm used to plug the HDD, add it to the RAID array while drinking coffee and forget about it. Now I got this new rig and I really wanna make the switch to Ubuntu. The absence of GUI is not a problem as I'm willing to learn how to use the command lines efficiently (and I find it kinda fun), but I'm overwhelmed with all the different variables and concepts that I never encountered on WHS.

I found a few guides out there, but none are using the UUIDs (which seems to be the new and best way to add drives-?). I followed [this]("https://help.ubuntu.com/community/InstallingANewHardDrive"), but I read that fdisk will not let me deal with volumes larger than 2TB.

> **darkod said:**
> [COLOR=#000000]If it's from ubuntu, it's not really a good practice to start partition on sector 1. If working in MiB, you should leave 1MiB unallocated at front.[/COLOR]
[COLOR=#000000]If working in sectors that are 512B like in your case, that would mean 2048 sectors, that would be the start point of the first partition.[/COLOR]

[COLOR=#000000]On top of that, on gpt disks ubuntu needs a small 1MiB partition with NO filesystem and the bios_grub flag set, so that it can install grub2 properly to the disk.[/COLOR]

[COLOR=#000000]And try using the command line and parted for the disk partitioning, webmin can be real pain. In fact, I would stay away from it, as much as having a GUI tool looks appealing. It often touches the config files in a different, specific way.[/COLOR]

[COLOR=#000000]Partitioning in the command line is very easy, no matter the setup you want to achieve. If you have an idea what you want to do, we can help with specific commands in the command line.[/COLOR]

Thanks for the input and yes, I'd love some help. If you could walk me through the first drive, so I can have fun adding my truckload of HDDs on my own :p. Basically these drives are pooled and hold my medias (HD movies, music, photos and whatnot), that I stream on my home network and sometimes over the web. The drives are a mix of WD30EZRX and ST4000DM000.

I also have some NTFS drives holding data that'd like to transfer onto the newly formated ext4 drives. But I don't know if that's possible. If it is, it'll be the object of a part 2.

> **darkod said:**
> [COLOR=#000000]I'm not familiar with FlexRAID myself. Is that like software raid, like mdadm?[/COLOR]

Pretty much. It's a software RAID that offers a neat snapshot/real-time RAID + storage pooling solution. I'm using it to protect my medias with nightly snapshots.

Again, thank you both. I just can imagine how painful it must be to deal with complete newbies such as me!

---

### Post by darkod on 2013-04-04
I prefer parted on the command line since it offers great flexibility. For example, to enter the parted prompt you would do:
```
sudo parted /dev/sda
```

One thing you have to be careful about is that parted usually does the changes right away, so make sure you get the command right. There is no green button to click to execute the changes like in Gparted (the GUI front of parted).

Since you will be using a type of SW raid most probably grub2 will need to be on the MBR of the physical disks (as ubuntu sees them). For gpt disks you need a small 1MiB partition with bios_grub flag, and NO filesystem (DO NOT format it with anything).

Once you get into the parted prompt with the command above, the basic commands are:
mklabel msdos/gpt - write a new blank msdos or gpt table
unit <unit> - set unit size that parted will use in subsequent commands, I most often use MiB MibiByte
mkpart <label> <start> <end> - make a gpt partition with label, start and end points, start and end are numbers in the unit size you have specified
set <number> <flag> on/off - set the flag on or off on partition number #
print - print some basic disk data and the current layout

So, writing a new gpt table on /dev/sda, setting the unit size in parted, making one small 1MiB partition starting from 1MiB (leaving 1MiB unallocated at front) and setting the bios_grub flag would be:
```
sudo parted /dev/sda
unit MiB
mkpart GRUB 1 2
set 1 bios_grub on
quit
```

That's it. Making other partitions is up to you. The most often unit size would be sector, MiB and GiB I guess. You can use the 'print' command to print the details and table in any moment. At the top in the details it will also show the disk size in the current unit (if the current unit is MiB it will show the total disk size in MiB and it can help you calculate your partition sizes and where the last one should end).

parted is also very suitable for making partitions for mdadm or similar SW raid since it makes only a partition, no filesystem. And that is exactly how SW raid uses partitions, without a filesystem on them since the filesystem is formatted on the raid device/array.

To use the partition in ubuntu as ext4 for example, you would need to do like:
sudo mkfs.ext4 /dev/sda2

to make a filesystem on it.

That should be enough to get you started. :)

---

### Post by lakz on 2013-04-04
Got it, *parted*. That is exactly what I needed, simple step by step instructions with clear explanations. Thanks.

One thing though. FlexRAID is not a file system but instead sits on top of an existing file system.

> [COLOR=#000000][FONT=sans-serif]FlexRAID does not mandate its own file-system; instead, it allows users to use any file-system, on which it builds its own lightweight file-system. FlexRAID leaves the file management aspect to the underlying file-system but keeps a copy of relevant file-system information.
[/FONT][/COLOR]
[COLOR=#000000][FONT=sans-serif]FlexRAID aims to be easier to implement than traditional RAID systems that work at the disk block level since the blocks are continuous and easy to manage. Nevertheless, that simplicity comes at the cost of the RAID system being unaware of the logical aspect of the data it is hosting.[/FONT][/COLOR]

I'm gonna double check on the FlexRAID forums.

---

### Post by lakz on 2013-04-04
-

---

### Post by lakz on 2013-04-04
Disregard my previous post. I was doing it wrong.

The FlexRAID forum is not very active and no one got back to me... I'm not sure whether a File System is needed or not, but their Wiki seems to suggest it.

**Question :** Why would I need a grub partition? I already have Ubuntu on the virtual drive /sda. These new disks will simply hold data.

---

### Post by lakz on 2013-04-04
I decided to format both disks with one large ext4 partition each and see how it goes. I used GParted.

Back on Putty, *sudo fdisk -l*, this is what I get :

> WARNING: GPT (GUID Partition Table) detected on '/dev/sdb'! The util fdisk doesn't support GPT. Use GNU Parted.



Disk /dev/sdb: 4000.8 GB, 4000787030016 bytes
255 heads, 63 sectors/track, 486401 cylinders, total 7814037168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x00000000


   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1  4294967295  2147483647+  ee  GPT
**Partition 1 does not start on physical sector boundary.**


WARNING: GPT (GUID Partition Table) detected on '/dev/sdc'! The util fdisk doesn't support GPT. Use GNU Parted.




Disk /dev/sdc: 3000.6 GB, 3000592982016 bytes
255 heads, 63 sectors/track, 364801 cylinders, total 5860533168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x00000000


   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1  4294967295  2147483647+  ee  GPT
**Partition 1 does not start on physical sector boundary.**


With parted :
> Model: ATA ST4000DM000-1F21 (scsi)Disk /dev/sdb: 4001GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt


Number  Start   End     Size    File system  Name  Flags
 1      1049kB  4001GB  4001GB  ext4




Model: ATA WDC WD30EZRX-00M (scsi)
Disk /dev/sdc: 3001GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt


Number  Start   End     Size    File system  Name  Flags
 1      1049kB  3001GB  3001GB  ext4


[B]Partition 1 does not start on physical sector boundary.
[/B]
Under GParted, the first sector for sdb and sdc is 2048, why do I get different numbers in Ubuntu?

This whole thing is really getting frustrating. I spent the day trying to get a HDD working...


[COLOR=#b22222][U][B]EDIT
[/B][/U][/COLOR]
I tried :
>  sudo parted /dev/sdb align-check optimal 1
1 aligned


 sudo parted /dev/sdc align-check optimal 1
1 aligned


:confused:

---

### Post by darkod on 2013-04-05
Which different numbers are you talking about? If you are referring to the fdisk output you can clearly see the warning that fdisk doesn't support gpt. That's why it's saying Partition 1 doesn't start on cylinder boundary.

On gpt disks as you have, use parted -l instead of fdisk -l. Forget about fdisk on gpt disks.

I don't understand why you say you wasted so much time. The disks/partitions look fine. From there on, how FlexRAID works I have no idea. :)

PS. If you want to use mdadm raid, I can help with that.
As for the previous question about the grub partition, you don't need it if you never plan to put grub2 on the MBR of these disks. But on another hand, since we are talking only about 1MiB space, it's sometimes good to have it in case you decide to put grub2 on the disks in future and use them differently. Without that partition, you would have to repartition the disk.

---

### Post by lakz on 2013-04-05
[COLOR=#000000][FONT=Arial]My bad, I will disregard fdisk. As for parted, the [/FONT][/COLOR][COLOR=#000000]1049KB was bothering me. Then [/COLOR][COLOR=#000000][FONT=Arial]I realized that for libparted a kilobyte is not equal to 1024 bytes, instead, is equal to 1000 bytes. 
[/FONT][/COLOR]
> [COLOR=#000000][FONT=Arial]**sudo** [/FONT][/COLOR]**parted /dev/sdb unit b print**

Number  Start        End                    Size                   File system  Name  Flags
 1          1048576B  4000786153471B  4000785104896B  ext4

[COLOR=#000000][FONT=Arial]
[/FONT][/COLOR]1048576B is 1MiB (1048576B ~= 1049KB)

1048576/2048 = **512 byte**. So yeah, it all makes sens now :D. 


Okay so now that's what I was talking about in the OP. Where and how do I properly mount these two disks with their UUIDs?


Ps: It's not what I meant by frustrating. Coming from windows, I'm used to the [COLOR=#333333][FONT=arial]gooey [/FONT][/COLOR]GUI environment and plug-and-play kind of things. What used to be overlooked in Windows in now a bit more work in Ubuntu, and the feeling on being stuck on something that simple is very undermining. But don't get me wrong, I love it, despite the learning curve. There's a first time for everything! I actually feel pretty darn good about having have successfully partitioned a disk \\:D/

---

### Post by oldschoolgentoo on 2013-04-05
Just curious have you looked into  LVM  [https://wiki.ubuntu.com/Lvm](https://wiki.ubuntu.com/Lvm)  instead of  Flexraid?  Or you can use  Mdadm raid like Drako mentioned.

---

### Post by darkod on 2013-04-05
Again, I don't know how FlexRAID works.
But for mounting the partitions directly, you have two approaches. You can use /dev/sdb1 and /dev/sdc1, or their UUIDs.

Using /dev/sdb1 will work but only if you don't move disks so that they get different letter in the ordering. Since this is a VM, this is unlikely. The UUID will work regardless of moving disks, as long as you don't reformat the partition because it gets the UUID during formatting.

Since you have ext4 on both partitions, the lines you need to add in /etc/fstab are like:
```
/dev/sdb1   /mountpoint1   ext4   defaults   0   2
/dev/sdc1   /mountpoint2   ext4   defaults   0   2
```

The mount point is a simple folder and can be named what ever you want. You have to create it first, only once (not on every boot of course). You will find the mounted partitions at /mountpoint1 and /mountpoint2.

Using the UUID would be the same only you replace /dev/sdb1 (and /dev/sdc1) with UUID=<string>.

You can get the UUIDs of all partitions with:
sudo blkid

---

### Post by lakz on 2013-04-05
> **oldschoolgentoo said:**
> Just curious have you looked into  LVM  [https://wiki.ubuntu.com/Lvm](https://wiki.ubuntu.com/Lvm)  instead of  Flexraid?  Or you can use  Mdadm raid like Drako mentioned.

I had no idea of what LVM was, but it looks very [interesting]("http://www.routemybrain.com/understanding-the-concept-of-logical-volume-manager-%E2%80%93-lvm/"). Particularly the hot-swapping possibilities. However, if a disk in a LVM Logical Volume Group fails, the whole group is corrupted.

FlexRAID can create a storage pool spanning the disks, which creates one massive logical volume. FlexRAID will also protect any type of *Data Risk Unit*, DRU, as long as the *Parity Protection Unit*, PPU, is the largest volume in the array. That means that DRUs can be a mix of any sizes and types, will all be pooled and protected (it could very well be a HDD, a network storage, a USB stick, anything!). Ultimately, a single PPU can in theory support an unlimited number of DRU (of course, additional PPUs are possible for more redundancy). These are the reasons why I stuck and have been very happy with FlexRAID :)

And in my case, the data in not changing much. Hence snapshot RAID makes much more sense.

---

### Post by oldschoolgentoo on 2013-04-05
> **lakz said:**
> I had no idea of what LVM was, but it looks very [interesting]("http://www.routemybrain.com/understanding-the-concept-of-logical-volume-manager-%E2%80%93-lvm/"). Particularly the hot-swapping possibilities. However, if a disk in a LVM Logical Volume Group fails, the whole group is corrupted.

the use of Mirror in LVM  covers that loss of a drive. command to recover after dead drive replaced in LVM >   vgcfgrestore   i should of put that in  my post about LVM.   I will  look into  Flexraid.  sounds interesting...

---

### Post by lakz on 2013-04-05
I read that using UUIDs is preferable because disk letters can be shuffled at boot. Anyways, I created the directories (**/p1** and **/d1**).

Just to make sure, I manually mounted the first drive using ***sudo mount UUID=theuuid /p1***. I can now see it in FlexRAID (almost there!).

However I tried to modify /etc/fstab.
***nano /etc/fstab***
Added the line : ***UUID=theuuid   /p1   ext4   defaults   0   2***

When I save and exit, I get :
[I][B]Error writing /etc/fstab: Permission denied

[/B][/I]:confused:

---

### Post by darkod on 2013-04-05
sudo nano /etc/fstab

You need sudo rights to modify fstab.

---

### Post by lakz on 2013-04-05
> **darkod said:**
> sudo nano /etc/fstab

You need sudo rights to modify fstab.

Yeah I actually used **sudo nano /etc/fstab**. I forgot to mention it...

I tried **sudo nano -Bw /etc/fstab** and have been able to modify fstab. The HDDs are mounted at boot :). Success! THANK YOU SO MUCH DARKOD.

I have a question : in [this](http://www.ghacks.net/2009/09/10/add-a-second-drive-to-your-ubuntu-server/) guide, they talk about using ***sudo chmod -R 777 /"disk folder"*** to make it available to all users. Is that necessary?

---

### Post by darkod on 2013-04-05
If FlexRAID only "assembles" the mount points, it might be. Otherwise the linux filesystem permisions will block other users from having write permisions.

---

### Post by spynappels on 2013-04-05
If the disks were to be used as plain data disks, you can define in the fstab who the owner/group of the mounted partition is. Look in the man page for the owner and group options. This will also works for volumes mounted from NFS,

---

### Post by lakz on 2013-04-05
> **darkod said:**
> If FlexRAID only "assembles" the mount points, it might be. Otherwise the linux filesystem permisions will block other users from having write permisions.

Am I not the only user? root=super user (me)=admin

> **darkod said:**
> [COLOR=#000000]If the disks were to be used as plain data disks, you can define in the fstab who the owner/group of the mounted partition is. Look in the man page for the owner and group options. This will also works for volumes mounted from NFS,[/COLOR]

I [looked]("http://en.wikipedia.org/wiki/Fstab#Common_options_to_all_filesystems") at the fstab options. Is it what you're talking about?

---

### Post by darkod on 2013-04-05
Well, the first user has sudo right by default. But when you asked if you chould run chmod 777 to make it available to all users, I assumed you will create more later.

Additional users don't have sudo rights by default and it's usually better not to have them. So, if you want other users accessing those folders, you need to give them rights.

---

