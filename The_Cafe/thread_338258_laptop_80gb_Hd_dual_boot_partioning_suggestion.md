---
title: "laptop 80gb Hd dual boot partioning suggestion"
date: 2007-01-14
forum: The Cafe
---

### Post by Gargamella on 2007-01-14
I wanna install in my laptop Edgy,my hd is 80 gb and I should use Winxp just for gaming (not more than 15 gb of game software)

I also have 10 gb of music on my laptop...so I may put this data on the windows partition and listen it on Ubuntu too,right?

anyway:

how would you make the partitions?:-k

---

### Post by Canis familiaris on 2007-01-14
I assume that you use the entire 80 GB in one partition is C: in Windows.
First, of all defragment your C: using the Disk Defragmentor Utility.
If after defragementation you see white space at the end of the drive, then job is done and next is to resize your C: partition.
Boot into Ubuntu/Kubuntu Live CD and run GParted/QTParted. Now right click /dev/hda1 and click resize.
Now resize C: as per usage, I recommend atleast 10 GB for Ubuntu, 1 GB for swap and anoher 10 GB Maybe for Music/Movies. 
Now restart into Windows and go to:
Control Panel->Administrative Tools->Disk Management
Create one maybe 10 GB partition which you desire for movies/music as X: (or any drive letter)
Format the new partition using FAT32, yes only FAT32!!!
Right Click on the black graph and create an extended partition to take over rest of the disk.
Restart and boot into Ubuntu/Kubuntu Live CD.
Click on install and make sure you select 'use free space during partition'
Install Ubuntu/Kubuntu.
Now after installing Ubuntu, go to Terminal and issue command:
```
sudo nautilus /mnt

```
Create a new folder foldername
In Kubuntu, go to Konsole:
```
sudo konqueror /mnt

```
Create a new folder foldername
where foldername is name for folder, i suggest lin4music 8) 
Close nautilus/konqueror
In Terminal, type:
```
sudo nano /etc/fstab
```
Scroll to the last line and add the following line:
```
/dev/hda2     /mnt/foldername     vfat     noauto,user 0 0
```
The /dev/hda2 can differ, please view in GParted/QTParted.
Type Crtl+O, save and Crtl+X to exit.
Type exit to terminal.
Now you can access your media in /mnt/foldername which is D: in Windows
Of course you have to copy your media to D:

:-k C: cant be accessed since i''m assuming it's formatted with ntfs

---

### Post by Gargamella on 2007-01-14
> **Anurag_panda said:**
> 
:-k C: cant be accessed since i''m assuming it's formatted with ntfs

yes it is,

so summaring, I will have 

first the Win ntfs partition
then the fat32 for shared data between oss
swap
ext3 for ubuntu

my friend always tells me that this partitiong is unhealthy for the hd,isn't it?

anyway it seems to me the better way

---

### Post by Gargamella on 2007-01-14
I now rezised the ntfs and I was going to make the fat32 partition...but when I create the new partition I can only format it with the ntfs file system...what to do?

---

### Post by migla on 2007-01-14
I always make a separate /home partition, so that I can keep media and settings even if I do a fresh installation in the future.

---

### Post by Canis familiaris on 2007-01-15
In case you use GNOME, using my above tip, you have to type mount command every time to access your shared file. In that case try this line instead:
```
/dev/hda2 /foldername vfat uid=anurag,gid=anurag 0 0
```
replace anurag by your username.
Note: this will only work within your usename.
In that case add other user within your group.
In KDE, you can simply go to System->Storage Media-> <your drive label older> to access your files.;)

---

### Post by Canis familiaris on 2007-01-15
> **Gargamella said:**
> yes it is,
my friend always tells me that this partitiong is unhealthy for the hd,isn't it?
anyway it seems to me the better way

Your friend is wrong. Such partitoining is as such not unhealthy. 

> **Gargamella said:**
> I now rezised the ntfs and I was going to make the fat32 partition...but when I create the new partition I can only format it with the ntfs file system...what to do?
To format in FAT32, just scroll down in the New Partition Wizard in Disk Management when if offers NTFS and select FAT32.
And yes, i suggest to create the root partition, swap, and perhaps the seperate /home, /usr partitions as logical drives in the extended partition.

---

### Post by Gargamella on 2007-01-15
I googled a bit around the net and I discovered what I was doing wrong...I can't make a Fat32 more than 30Gb in my situation...so I was only able to make a ntfs...

gonna install edgy, see you later ;D

thank you

---

### Post by Gargamella on 2007-01-15
I am here to report a question:

I made the fat32 partition and it works...but also the ntfs is accessible too from ubuntu!
so I think I am going to delete the fat32 to use the data directly from the nfts...
is this a good idea?

---

### Post by Canis familiaris on 2007-01-15
Bad idea!!! the NTFS access in ubuntu is read only and the packages which allow to write NTFS, cannot be relied upon completely. If you are so keen on using your C: as shared drive, then convert it into FAT32 using powerquest partition magic.

---

### Post by Gargamella on 2007-01-15
not so keen...I will leave the fat32 here where it is ;D

thanks

---

### Post by maniacmusician on 2007-01-15
actually ntfs3g is pretty stable now, including write support, so he shouldn't have anything to worry about.

---

### Post by Canis familiaris on 2007-01-16
Yeah maybe, but this may risk endangering his Windows installation, perhaps by mistake he deletes system files, then. It is always suggested if you dual boot with windows keep the windows system partition separate from shared partition b/w linux and windows.

---

### Post by maagimies on 2007-01-16
I usually create an **ext2** partition for shared data between Windows and Linux, and then use [http://www.fs-driver.org/](http://www.fs-driver.org/) in Windows.
It's a driver for ext2, so the partition will be used like a regular drive. With read&write support.

---

