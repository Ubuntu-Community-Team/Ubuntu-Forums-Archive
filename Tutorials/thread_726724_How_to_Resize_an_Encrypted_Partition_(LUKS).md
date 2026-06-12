---
title: "How to: Resize an Encrypted Partition (LUKS)"
date: 2008-03-17
forum: Tutorials
---

### Post by bodhi.zazen on 2008-03-17
[center][size=6]**How to Resize a LUKS Encrypted File System.**[/center][/size]

[center][img]http://www.puzzlesolver.com/data/86/images/1.gif[/img][/center]


[size=2]**Contents[/size]**
[list=number][*]Introduction.
[*]Terminology.
[*]Setup Live CD to manage encrypted partitions.
[*]Resizing ~ Overview.
[*]Resizing in detail ~ Reduction.
[*]Resizing in detail ~ Enlargement
[*]References.[/list]



_Introduction_: Encryption seems to becoming more popular and one can install onto an encrypted hard drive with the Alternate CD.

> Guided - use entire disk and set up encrypted LVM

There is no (obvious) option to add additional partitions such as either a /home or /data partition. *Now a big part of this problem can be solved if you understand the partitioning options on the Alternate CD, I will save that for another how-to ....*

In the mean time, see this link : [http://users.piuha.net/martti/comp/ubuntu/en/cryptolvm.html](http://users.piuha.net/martti/comp/ubuntu/en/cryptolvm.html)


Worse, I could not find any documentation on how to resize the encrypted partition after the installation :( .

**Resizing your encrypted file system can not be done directly as of yet with Gparted as Gparted sees the encrypted partitions as unformatted space.**

**At this time, the crypt must be re-sized from a live CD in multiple steps, manually, from the command line.**

**It should go without saying, resizing your crypt may result in data loss :( Be sure to [color=red]BACK UP[/color] your data first.** :twisted:

It may be easier to simply reinstall following the link above. Here it is again :

[http://users.piuha.net/martti/comp/ubuntu/en/cryptolvm.html](http://users.piuha.net/martti/comp/ubuntu/en/cryptolvm.html)

For this how-to I used the default partitioning/encryption scheme. The LUKS crypt is called "crypt1" and I called the LV group "hardy" (the installer defaults to your hostname).


[size=4]**Terminology[/size]**

Compartments within compartments.

LUKS = Linux Unified Key Setup.

While a detailed explanation of either LVM or encryption is beyond this how to, think of  an encrypted system we have multiple containers, the crypt and LVM, and the file system. We need to resize each of those.

[list][*]Physical partition.
[*]Crypt.
[*]LVM -> 
[list][*]Physical Volume.
[*]Logical Volume.[/list]
[*]File system.[/list]

_Physical partition_ -> This is a partition on your hard drive to contain the LUKS crypt (The Alternate CD defaults to /dev/sda5 for encryption).

_Crypt_ = LUKS then creates a crypt within the physical partition. The contents of the crypt are, of course, encrypted. The encrypted space is mapped to /dev/mapper/crypt1 , LVM is then used to create partitions within the crypt.

_LVM_ = Logical Volume Management. LVM takes physical partitions (AKA Physical Volumes) and creates Logical Volumes, somewhat similar to a logical partition within an extended partition.

[indent]_Physical Volume_ The (LVM)  Physical Volume used for encryption is the LUKS crypt, which is mapped to /dev/mapper/crypt1.[/indent]

[indent]_Logical Volumes_ The (LVM) Physical Volume is divided into (LVM) Logical Volumes which are in turn used for / (root partition) and swap. Similar to logical partitions, these are contained within the (LVM) Physical Volume within (LUKS) crypt within the physical partition.[/indent]

_File system_ = ext3 (or swap) = The actual file system written onto the logical volumes.


Start by knowing your root partition and how you want to resize. Some helpful commands include :

```
df -h

sudo blkid

sudo fdisk -l

sudo cryptsetup status crypt1

sudo pvdisplay

sudo lvdisplay

mount

free
```

  
[size=4]**Setup ~ Desktop (Live) CD, Adding the tools to manage encrypted partitions**[/size]

1. Boot the live (Desktop) CD and install  lvm2 and cryptsetup.

```
sudo apt-get update && sudo apt-get install lvm2 cryptsetup
```

2. Load the cryptsetup module.

```
sudo modprobe dm-crypt
```

2. Decrypt your file system.

```
sudo cryptsetup luksOpen /dev/sda5 crypt1
```

4. Get the live CD to recognize (activate) your LVM.

```
sudo vgscan --mknodes
sudo vgchange -ay
```

You can now manage your encrypted partitions, mount them, copy them, or perform maintenance (fsck, backup, resize).


[size=4]**Resizing ~ Overview**[/size]

The order of the next steps depends on if you are shrinking or enlarging your encrypted partition. Enlarging is somewhat easier as the defaults of many of the commands is to fill the available space.

[indent]_Note_: If you want to Enlarge your encrypted partition, although adding a second  physical hard drive to LVM is "easy" I am not sure you could then add this to your Crypt (the Crypt must be on a single hard drive).[/indent]

**Shrink an encrypted partition**
[list=number][*]Boot the desktop, live CD. Install & configure the tools (lvm2 and cryptsetup).
[*]Reduce the (root) file system with ***resize2fs***.
[*]Reduce the (root) (LVM) Logical Volume with ***lvreduce***.
[*]Reduce the (LVM) Physical Volume with ***pvresize***.
[*]Reduce the Crypt with ***cryptsetup***.
[*]Reduce the Partition storing the crypt with ***fdisk***.
[*]Reboot to your encrypted hard drive ~ You should always reboot after changing your partition table with fdisk.[/list]

**Enlarge an encrypted partition**
[list=number][*]Boot the desktop, live CD. Use gparted (or any tool) to put unallocated space adjacent, and to the left of your Crypt partition.
[*]Enlarge the Partition storing the crypt with ***fdisk***.
[*]Reboot ~ You should always reboot after changing your partition table with fdisk.
[*]Boot the desktop, live CD. Install & configure the tools (lvm2 and cryptsetup).
[*]Enlarge the Crypt with ***cryptsetup***.
[*]Enlarge the (LVM) Physical Volume with ***pvresize***.
[*]Enlarge the (root) (LVM) Logical Volume with ***lvresize***.
[*]Enlarge the (root) file system with ***resize2fs***.
[*]Reboot to your encrypted hard drive.[/list]


**[size=4]Detailed resizing ~ Shrinking an encrypted partition[/size]**

1. Reduce the size of your file system with resize2fs (this tool works on ext2 and ext3 partitions). You need to check the file system before you can resize it.

```
sudo e2fsck -f /dev/mapper/hardy-root
sudo resize2fs -p /dev/mapper/hardy-root 5g
```

[list][*]Replace the "5g" with your intended size (in Gb) of your filesystem.
[*]The -p flag shows a progress hash.[/list]

Check that the file system is still intact with e2fsck.

```
sudo e2fsck -f /dev/mapper/hardy-root
```


2. Reduce the size of your root (LVM) Logical Volume. The -L flag is how much you want to reduce the size of your (LVM) Logical Volume, so keep this in mind.

Display your (LVM) Logical Volumes with lvdisplay.

```
sudo lvdisplay
```

Note how much you need to reduce your root (LVM) Logical Volume by (in my case it was 4.3 Gb).

```
sudo lvreduce -L -4.3G /dev/hardy/root
```

[indent]_Note_: You will need to change the "-4.3G" to the proper size to reduce your root (LVM) Logical Volume to your desired size.[/indent]

Re-display your (LVM) Logical Volumes to check the final size is correct.

```
sudo lvdisplay
```


3. Resize your (LVM) Physical Volume.

Remove the swap (LVM) Logical Volume. The (LVM) Physical Volume used by LVM can become "fragmented" in that the (LVM) Logical Volumes within the (LVM) Physical Volume are not always in order. There is no defragmentation tool, so if you may need to manually move the (LVM) Logical Volume (back up the data, delete the (LVM) Logical Volume, re-create a replacement (LVM) Logical Volume, restore data from backup).  

Show the size of your (LVM) Physical Volume with pvdisplay.

```
pvdisplay
```

Remove the swap (LVM) Logical Volume.

```
lvremove /dev/hardy/swap_1
```

Resize the (LVM) Physical Volume.

```
sudo pvresize --setphysicalvolumesize 5.6G /dev/mapper/crypt1
```

Now we will restore (recreate) the swap (LVM) Logical Volume.

Set permissions of (LVM) Physical Volume to allow allocation (if needed).

```
sudo pvchange -x y /dev/mapper/crypt1
```

Restore the swap (LVM) Logical Volume.

```
sudo lvcreate -L 512m -n swap_1 hardy
sudo mkswap -L swap_1 /dev/hardy/swap1
```

[indent]As the mkswap command finishes it will print the new uuid to the terminal.[/indent]

Update fstab with new uuid (use any editor).

```
sudo mount /dev/hardy/root /mnt
```

```
gksu gedit /mnt//etc/fstab
```

Copy-paste the new uuid from the terminal to fstab, updating the uuid for your swap partition.

Save and exit gedit.

Unmount the root (LVM) Logical Volume.

```
sudo umount /mnt
```

Re-lock the (LVM) Physical Volume after adding the swap (LVM) Logical Volume (locking the physical volume keeps it from changing).

```
sudo pvchange -x n /dev/mapper/crypt1
```


4. Resize your crypt.

Show the size of your crypt with cryptsetup.

```
sudo cryptsetup status crypt1
```

This shows the size of your crypt in sectors.

Make note of the offset.

> offset:   2056 sectors

Resize with cryptsetup.

```
sudo cryptsetup -o 2056 -b 11800000 resize crypt1
```

-o = offset (get this from the status command).
-b = size in sectors. I had to do this by trial and error. After resizing I used Gparted to show the size of the crypt (System -> Administration -> Partition Editor ; select /dev/mapper/crypt1 from the pul down menu). Close gparted after confirming the new size of your crypt.


5. Resize your partitions with fdisk.

Unmount your LVM and crypt.

```
sudo vgchange -an
sudo cryptsetup luksClose crypt1
```

Now the scary part, use fdisk to manually resize your partitions.

[color=red]If you are unfamiliar with fdisk, I advise you read this link.[/color]

[http://tldp.org/HOWTO/Partition/fdisk_partitioning.html](http://tldp.org/HOWTO/Partition/fdisk_partitioning.html)

Note : fdisk does NOT overwrite data, so if you make a mistake you should be able to "undo" the changes.

List your partition information with fdisk.

```
sudo fdisk -l
``` 

**WRITE THIS INFORMATION DOWN** (or print it out).

Re-write your partition table. To do this, DELETE your partitions and RECREATE them, but in a smaller size.

You will need to delete and re-create ALL your LVM partitions within your crypt.

```
sudo fdisk /dev/sda
```

This was my fdisk session :

> The number of cylinders for this disk is set to 1305.
There is nothing wrong with that, but this is larger than 1024,
and could in certain setups cause problems with:
1) software that runs at boot time (e.g., old versions of LILO)
2) booting and partitioning software from other OSs
   (e.g., DOS FDISK, OS/2 FDISK)

Command (m for help): d
Partition number (1-5): 5

Command (m for help): d
Partition number (1-5): 2

Command (m for help): n
Command action
   e   extended
   p   primary partition (1-4)
e
Partition number (1-4): 2
First cylinder (32-1305, default 32): 
Using default value 32
Last cylinder or +size or +sizeM or +sizeK (32-1305, default 1305): +6000M

Command (m for help): n
Command action
   l   logical (5 or over)
   p   primary partition (1-4)
l
First cylinder (32-761, default 32): 
Using default value 32
Last cylinder or +size or +sizeM or +sizeK (32-761, default 761): 
Using default value 761

Command (m for help): n
Command action
   l   logical (5 or over)
   p   primary partition (1-4)
p
Partition number (1-4): 3
First cylinder (762-1305, default 762): 
Using default value 762
Last cylinder or +size or +sizeM or +sizeK (762-1305, default 1305): 
Using default value 1305

Command (m for help): p

Disk /dev/sda: 10.7 GB, 10737418240 bytes
255 heads, 63 sectors/track, 1305 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000a6bf9

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          31      248976   83  Linux
/dev/sda2              32         761     5863725    5  Extended
/dev/sda3             762        1305     4369680   83  Linux
/dev/sda5              32         761     5863693+  83  Linux

Command (m for help): w
The partition table has been altered!

Calling ioctl() to re-read partition table.
Syncing disks.

Cancel the "Authentication" dialog that appears (the live CD is trying to auto-mount your new partition).


<Say prayer here> [-o<

Reboot to your hard drive, enter your crypt password.


[size=4]**Detailed resizing ~ Enlarging an encrypted partition.[/size]**

This section will be shorter, it is basically the reverse of the above. Enlarging is easier as the defaults resize the containers to the largest available space.

1. Boot a live CD and, using any tool, create a new partition, lets call it **/dev/sda6** , next to and to the left of (after) your crypt.

2. Write random data to the new partition.

[indent][color=red]**Make sure you have the correct partition for this command or you will overwrite your crypt.**[/color][/indent]

```
sudo dd if=/dev/urandom of=**/dev/sda6**
```

[indent]You can run that command as many times as your paranoia requires. :twisted:[/indent]

3. Use fdisk as above to delete and then re-create a larger crypt partition.

4. Reboot to the live CD.

5. Install lvm2 and cryptsetup.

```
sudo apt-get update && sudo apt-get install lvm2 cryptsetup
```

6. Load the cryptsetup module.

```
sudo modprobe dm-crypt
```

7. Decrypt your file system.

```
sudo cryptsetup luksOpen /dev/sda5 crypt1
```

8. Get the live CD to recognize (activate) your LVM.

```
sudo vgscan --mknodes
sudo vgchange -ay
```

9. Resize the Crypt.

```
sudo cryptsetup resize crypt1
```

10. Resize the (LVM) Physical volume.

```
sudo pvresize /dev/mapper/crypt1
```

11. Resize your root (LVM) Logical Volume.

Unlock the physical volume.

```
sudo pvchange -x y /dev/mapper/crypt1
```

Resize your root (LVM) Logical Volume.

```
lvresize -L +4G /dev/hardy/root
```

[indent]_Note_: Change the +4G to the amount of space you are adding.[/indent]

Re-lock the (LVM) Physical Volume.

```
sudo pvchange -x n /dev/mapper/crypt1
```

12. Resize the filesystem.

```
sudo e2fsck -f /dev/mapper/hardy-root
sudo resize2fs -p /dev/mapper/hardy-root
```

You can check the size of the file system by mounting it **before and after** resizing the file system and running df -h . [color=red]**DO NOT RESIZE A MOUNTED PARTITION**[/color]

Before :> Filesystem          Size  Used Avail Use% Mounted on
/dev/mapper/hardy-root              **5.0G**  2.1G  2.7G  45% /mnt

After :> Filesystem            Size  Used Avail Use% Mounted on
/dev/mapper/hardy-root              **9.2G**  2.1G  6.6G  24% /mnt

12. Reboot to hard drive.

_Note_ : With most of those commands the default was to resize by expanding to take up the available space. This is why expanding is easier then reducing.


[font=times][size=4][i]Hope this helped,[/size][/font]

[img]http://img381.imageshack.us/img381/4226/xubuntulogo2small0lj.png[/img][size=4] [color=navy][font=times]bodhi.[/color][color=darkgray]zazen[/font][/size][/color][/i]


**References :**

_LUKS wiki page_ :
[http://www.saout.de/tikiwiki/tiki-index.php?page=ResizeLUKSPartitions](http://www.saout.de/tikiwiki/tiki-index.php?page=ResizeLUKSPartitions)


_Managing encrypted partitions from a live CD_ :
[http://www.ubuntugeek.com/rescue-an-encrypted-luks-lvm-volume.html](http://www.ubuntugeek.com/rescue-an-encrypted-luks-lvm-volume.html)
[http://linuxwave.blogspot.com/2007/11/mounting-lvm-disk-using-ubuntu-livecd.html](http://linuxwave.blogspot.com/2007/11/mounting-lvm-disk-using-ubuntu-livecd.html)

_man resize2fs_ :
[http://linux.die.net/man/8/resize2fs](http://linux.die.net/man/8/resize2fs)


_LVM_ : 
[list][*]Setup : [http://www.netadmintools.com/art365.html](http://www.netadmintools.com/art365.html)
[*]Extend: [http://www.netadmintools.com/art366.html](http://www.netadmintools.com/art366.html)
[*]Shrink: [http://www.netadmintools.com/art367.html](http://www.netadmintools.com/art367.html)
[*][http://www.spinics.net/lists/lvm/msg16476.html](http://www.spinics.net/lists/lvm/msg16476.html)
[*][http://www.debuntu.org/how-to-install-ubuntu-over-lvm-filesystem](http://www.debuntu.org/how-to-install-ubuntu-over-lvm-filesystem)[/list]


_fdisk_ : 
[list][*]
[*][http://www.enigmacurry.com/2007/04/28/resizing-a-luks-dm-crypt-cryptsetup-filesystem/](http://www.enigmacurry.com/2007/04/28/resizing-a-luks-dm-crypt-cryptsetup-filesystem/)[/list]

**_Note_ : the first (and only comment at the time of this post) on this blog reads** :

> **How to get the data back ?** 

:lolflag:

**[color=red]BACK UP before your Resize.[/color]**

---

### Post by shanepardue on 2008-03-22
Wow! Thanks for all the hard work in relaying this info!

---

### Post by petaramesh on 2008-05-27
Hi Bodhi, thanks for this useful article. I have experimented further and it *seems* that the "cryptsetup resize" might be useless for a LUKS partition, at is *seems* that it uses the complete available partition size anyway. After I enlarged a partition holding a LUKS container (and rebooted), "cryptsetup status" for the container gave me the exact same numbers *before* and *after* "cryptsetup resize", so I truly wonder if it is of any use. The LUKS container was actually bigger than previously, so I assume it worked "automagically" ;-)

Furthermore, I was able to successfully "hot extend" the encrypted LVM partition holding my complete live system *without* having to do it booting from a "live CD", but truly from the live system itself.

I actually describe the process in [an article at my ashram]("http://petaramesh.org/post/2008/05/27/Retailler-a-la-volee-une-LVM-chiffree-LUKS") (in french, Google Translate or Babel fish may help you getting a [truly poor translation into english]("http://translate.google.com/translate?u=http%3A%2F%2Fpetaramesh.org%2Fpost%2F2008%2F05%2F27%2FRetailler-a-la-volee-une-LVM-chiffree-LUKS&hl=fr&ie=UTF8&sl=fr&tl=en") ;-)

Thanks for your article again.

---

### Post by stiffmaster on 2008-07-01
thx a lot bodhi!! You saved me a lot of time !! This how-to works like a charm!:)

---

### Post by ShelJ on 2008-08-16
Alright, after prayer, what do I do if I cannot boot?  :'(

When I tried to reboot, the passphrase query did not pop up, and eventually the computer opened in commandline mode, and i couldn't do anything anyways.

EDIT:  nm, turns out that everything was erased and I have to reinstall.

---

### Post by cbonar on 2008-12-06
> Resize with cryptsetup.

```
sudo cryptsetup -o 2056 -b 11800000 resize crypt1
```

-o = offset (get this from the status command).
-b = size in sectors. I had to do this by trial and error. After resizing I used Gparted to show the size of the crypt (System -> Administration -> Partition Editor ; select /dev/mapper/crypt1 from the pul down menu). Close gparted after confirming the new size of your crypt.

First thank you very much for this tutorial, I successfully shrinked my luks partition without problem.

I would just like to add some informations about how to get the size when shrinking.

In my case I didn't make use of LVM so I had an ext2 volume directly inside my luks partition.

Therefore, the size to give to **"cryptsetup resize"** was the one of the shrinked ext2 volume, as given by the **"resize2fs"** command (the -M option is to automatically shrink the volume to the minimum size) :

```
sudo resize2fs -M -p /dev/mapper/bak
resize2fs 1.41.3 (12-Oct-2008)
Resizing the filesystem on /dev/mapper/bak to 7233658 (4k) blocks.
Begin pass 2 (max = 5347914)
Relocating blocks             XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX
Begin pass 3 (max = 746)
Scanning inode table          XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX
Begin pass 4 (max = 41)
Updating inode references     XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX
The filesystem on /dev/mapper/bak is now **7233658** blocks long.

```

You can convert the number of blocks into a number of sectors using a simple golden rule.

You can get the number of bytes per block with the command **"sudo tune2fs -l /dev/mapper/bak"**, for instance.
You can get the number of bytes per sector with **"fdisk"**, for instance.
I let you do the rest.


To know which size to give to fdisk for the new partition (it's a little bit bigger than the luks partition, I don't know the exact rule), I simply noted the size of the partition before the operation and reduced it by the same amount as the luks partition had been shrinked by.

It worked like a charm : I had a shrinked luks partition with 0 byte available (the goal, was to transfer its data to another partition, then delete it to recreate it somewhere else) :-)

---

### Post by chris2kn5 on 2008-12-17
Hi there! I wanted to know if this guide is correct for me or to guide me to accomplish something. Right now -- I currently have Ubuntu 8.10 full-disk encrypted LVM on the laptop. However, I'm trying to resize the HDD as to create free spaces for a new LVM + Cryptsetup + LUKS encrypted partition that I'd be able to access.

Should I be installing Ubuntu on regular LVM then from there, to resize the LV to...20G then create the new VG + LV for encrypted partition? Lot of partitions surely got me confused.

I only wanted to create a encrypted partition for my laptop (on one HDD) where I can storage my data in... in either encrypted LVM or regular LVM. Perhaps you can write a tutorial if you have the time? Please do advise. Thank you.

---

### Post by madmufflon on 2009-02-10
hey, 
unfortunately i have problems using cryptsetup resize. 
I'm trying to free some space for a windows installation.
i'm following the steps descriped here. But after the cryptsetup resize i have the following problem:

cryptsetup status shows the size the partition should have after the resize.
if i close the cryptpartition with cryptsetup luksClose the partition has its old size in fdisk and when i remount the partition using the harddiskdetection function of the alternate cd (im installing from an alternate cd) the encrypted partition has its old size.

any help is appreciated
thanks,  
martin

---

### Post by bodhi.zazen on 2009-02-10
> **madmufflon said:**
> hey, 
unfortunately i have problems using cryptsetup resize. 
I'm trying to free some space for a windows installation.
i'm following the steps descriped here. But after the cryptsetup resize i have the following problem:

cryptsetup status shows the size the partition should have after the resize.
if i close the cryptpartition with cryptsetup luksClose the partition has its old size in fdisk and when i remount the partition using the harddiskdetection function of the alternate cd (im installing from an alternate cd) the encrypted partition has its old size.

any help is appreciated
thanks,  
martin

Can you please give us more details ? What is your set up ? Are you using LVM ? What command did you enter and what output are you looking at ?

 Did you read cbonar's post ?

---

### Post by madmufflon on 2009-02-13
thanks for your answer,

i'm using the ubuntu 8.10 standart setup (installed via alternate cd), so I am using an LVM. 
I'm running a Dell Studio Notebook with a 250GiB harddisk. At the moment this harddisk is fully covered by my ubuntu 8.10 x64.

I followed the orders to shrink my encrypted partition until step 5:
```
5. Resize your partitions with fdisk.

Unmount your LVM and crypt.
```
When trying to resize the partition using fdisk i come to that point:
> Command (m for help): d
Partition number (1-5): 5

Command (m for help): d
Partition number (1-5): 2

Command (m for help): n
Command action
e extended
p primary partition (1-4)
e
Partition number (1-4): 2
First cylinder (32-1305, default 32):
Using default value 32
Last cylinder or +size or +sizeM or +sizeK (32-1305, default 1305): +6000M
(Other Values vor the cylinders, arround 70000 but only a short range) when i try to enter a value which fits for me (from 230 to arround 200gb) fdisk says something about "value out of range". Even for very small values (10gb or so) it does not work with the same error. 
If i let the harddiskrecognition of the Alernate CD detect the harddrives and mount the encrypted partition cryptsetup status sda5 says it has the old size ( the size before crpytsetup resize).

I hope this enough information, if not, please let me now
martin

---

### Post by ovizii on 2009-02-22
thx for the guide but I have a small question:

I made a single error, my swap is too big. I thought I could just unmount the swap while being logged into the swap and resize it. Unfortunately I can't seem to unmount it :-(

I tried swapoff -a which should unmount all swaps but when I want to resize I am told that it is in use :-(

any hints please?

after resizing the swap, I'd like to increase/reyize the / root partition, will this work while using the system or do I again need to boot from CD?

---

### Post by ovizii on 2009-02-22
ok, I brute-forced the swap to be resized. I was warned that data might be lost, but I didn't care about the swap :-)

what about resizing the / partition now using the free space I saved by resizing the swap partition?

can I stop the GDM, unmount the root "umount / " then use "lvextend -L+15G /dev/titan/titan-root" "e2fsck -f /dev/titan/titan-root" and "mount /" to do this?

---

### Post by bodhi.zazen on 2009-02-22
Are you running from a live CD ? It does not sound as if you are.

Why do you need to stop GDM ?

Otherwise this how to gives detailed step-by-step instructions on how to resize and those command are part, but not all, of what needs to be done.

---

### Post by ovizii on 2009-02-22
sorry for not being specific enough, what I wanted to know is if there is a way to resize my root partition inside a lvm group which now has enough free space because I resized my swap partition, while residing inside an encrypted partition, from within the live system

---

### Post by Flimm on 2010-04-02
I'm trying to enlarge an encrypted LVM to the left. Right now it's all the way to the right, so I can't expand it in that direction any longer.

Right now, I'm stuck at this step:
> 3. Use fdisk as above to delete and then re-create a larger crypt partition.

As I understand it, I'm supposed to use fdisk to delete the old partition location and recreate it with a larger size. However, I've read [here](http://www.linuxquestions.org/questions/fedora-35/lvm-partition-resizing-666683/) that you can only resize LVMs by expanding them to the right, based on this:
> WARNING: Make sure the old and new partition start at the same cylinder position, not doing so will destroy your data.

So what can I do? How do I resize an LVM partition to the left using fdisk?

---

### Post by bodhi.zazen on 2010-04-02
> **Flimm said:**
> I'm trying to enlarge an encrypted LVM to the left. Right now it's all the way to the right, so I can't expand it in that direction any longer.

Right now, I'm stuck at this step:


As I understand it, I'm supposed to use fdisk to delete the old partition location and recreate it with a larger size. However, I've read [here]("http://www.linuxquestions.org/questions/fedora-35/lvm-partition-resizing-666683/") that you can only resize LVMs by expanding them to the right, based on this:


So what can I do? How do I resize an LVM partition to the left using fdisk?

That I know of you can not do that. Gparted does not handle LVM either so most likely you are looking at backing up your data, deleting the LVM, make a new larger LVM / Crypt, restore your data.

---

### Post by Flimm on 2010-04-03
What about extending the volume group by adding physical volumes to it to the left? That's what [linux.com](http://www.linux.com/archive/feature/118645) seems to recommend:
> But what happens when your logical volume has taken up all the space in your volume group? You can add more physical volumes to an existing volume group, and then increase the size of your logical volume as discussed already.

First, unmount the logical volumes within your volume group. Assuming you already have physical volumes available, you can use the command vgextend home2 /dev/sda5 /dev/sda7 to add the physical volumes sda5 and sda7 to the existing volume group home2. The volume group home2 is now made up of sda3, sda5, and sda7

I'm not sure how encryption fits in though.

---

### Post by bodhi.zazen on 2010-04-04
In theory you could do that.

---

### Post by _Groove_ on 2010-07-06
Hi, I had a problem extending the LUKS partition.

* 64GB SSD -> 128GB SSD
* Recreated partitions on new SSD, made the LUKS partition fill the rest of the available space before the extended partition and boot partition at the end of the device
* used dd to copy the contents of the original disk partitions to the new partitions
* Used blockdev --getsize to find the number of sectors in the LUKS partition
* cryptsetup luksOpen /dev/sda1 sda1_crypt
* cryptsetup resize sda1_crypt --size NEWNUMBEROFSECTORS

Now, cryptsetup status shows the LUKS volume as having a size just a bit smaller than the new number of sectors I provided. However, pvresize does not do anything but exit 0. The PV is not resized. Any ideas what I'm doing wrong?

---

### Post by ubudog on 2010-07-24
Thanks for the tutorial.  Will this work in Lucid?  I see "hardy" in the shrinking section.  Thanks.

---

### Post by bodhi.zazen on 2010-07-24
> **ubudog said:**
> Thanks for the tutorial.  Will this work in Lucid?  I see "hardy" in the shrinking section.  Thanks.

I do not see any reason it would not work in lucid, the basics of file systems / crypts / LVM have not changed.

---

### Post by ubudog on 2010-07-24
Yeah, sorry.  I just realized what I had to do.  Thanks so much for this tutorial!

---

### Post by bodhi.zazen on 2010-07-24
> **ubudog said:**
> Yeah, sorry.  I just realized what I had to do.  Thanks so much for this tutorial!

No problem, hope it helped and that you go tit sorted.

---

### Post by ubudog on 2010-07-24
Yeah, it seems to be working right now.  Is is supposed to take this long?  I guess I'll let it do it over night.

---

### Post by bodhi.zazen on 2010-07-24
> **ubudog said:**
> Yeah, it seems to be working right now.  Is is supposed to take this long?  I guess I'll let it do it over night.

Depends on what step you are on and how large the partition is.

But yes. if it started, let it run. You are much much more apt to have problems if you interrupt it now.

---

### Post by ubudog on 2010-07-24
> **bodhi.zazen said:**
> Depends on what step you are on and how large the partition is.

But yes. if it started, let it run. You are much much more apt to have problems if you interrupt it now.

Ok, thanks.

---

### Post by ubudog on 2010-07-26
On step two of resizing (shrinking), you said that in your case it was 4.3g, but how do I find out how much I need to remove?  Thanks.

---

### Post by bodhi.zazen on 2010-07-26
> **ubudog said:**
> On step two of resizing (shrinking), you said that in your case it was 4.3g, but how do I find out how much I need to remove?  Thanks.

What is the current size of your LVM ? What size do you want it to en up as ?

Subtract those two numbers.

Current = 10 Gb
Desired = 6 Gb

Reduce the size by 4 Gb.

---

### Post by ubudog on 2010-07-26
But it doesn't have to be shrunk the same amount as in the previous step?  Sorry, I've never done anything like this.

---

### Post by bodhi.zazen on 2010-07-26
> **ubudog said:**
> But it doesn't have to be shrunk the same amount as in the previous step?  Sorry, I've never done anything like this.

yes

---

### Post by ubudog on 2010-07-26
On step 3 of shrinking, I get this error:
sudo pvresize --setphysicalvolumesize 48.81G /dev/mapper/crypt1 
  /dev/mapper/crypt1: cannot resize to 12495 extents as 25600 are allocated.
  0 physical volume(s) resized / 1 physical volume(s) not resized


What is that?  How do I fix it?  Thanks.

---

### Post by Hannes S on 2010-12-26
Hi,

thanks for the extensive howto! I got a new, larger hard disk for my laptop, copied the old disk byte-by-byte using dd onto the new one and proceeded along your tutorial to get the additional gigabytes into the home partition. 

Worked perfectly, thanks a lot!

 Hannes

---

### Post by bodhi.zazen on 2010-12-26
> **Hannes S said:**
> Hi,

thanks for the extensive howto! I got a new, larger hard disk for my laptop, copied the old disk byte-by-byte using dd onto the new one and proceeded along your tutorial to get the additional gigabytes into the home partition. 

Worked perfectly, thanks a lot!

 Hannes

glad it worked.

---

### Post by dgw on 2011-03-04
edit: nevermind. I messed up while trying to follow this tutorial so I'm just going to restore from my backup rather than trying to fix it, because I'm not getting anywhere trying to fix it.

---

### Post by fa2k on 2011-03-05
Thanks for the great tutorial, it worked perfectly.

---

### Post by steevven1 on 2011-05-01
Nice tutorial, but I have a question on how it applies to me. I installed Ubuntu 11.04 from the alternate CD using the whole disk as LUKS, but  Itold it to leave 80 GB free, thinking this would literally leave 80 GB unpartitioned on my drive, but it didn't. It seems to have left 80 GB free in the crypt (/dev/sda5 is the size of my entire HDD, but running "pvs" shows 80 GB free in the crypt area).

I'd like to shrink the crypt to be 80 GB smaller, thus leaving 80 GB of completely unpartitioned space on my drive. Which parts of the tutorial for shrinking the crypt should I follow? Just the last two?

Also, the part about using fdisk seems vague and scary. Any further advice on this? I've never used fdisk before.

Thank you!!!

---

### Post by bodhi.zazen on 2011-05-01
> **steevven1 said:**
> Also, the part about using fdisk seems vague and scary. Any further advice on this? I've never used fdisk before.

Thank you!!!

There are no gui tools to do this for you. You need to understand what each of the commands I gave you is doing.

You can work your way through the tutorial, but if you get stuck, it sounds as if this is a fresh install ? Just re-install and be careful of the size of your crypt when you partition, or partition the HD before you install and specify what partition to use as the crypt.

---

### Post by steevven1 on 2011-05-02
Okay, so I caved and just grew my encrypted partition to fill the size of the crypt instead of bothering with the partition outside the crypt. Your tutorial worked beautifully for this, thank you.

Now, here's a question: I have a 640 GB HDD, and when I installed 11.04 from the alternate CD, I told it to use the entire drive for the crypt, but my /boot partition is only 250 MB and my crypt is only 584 GB...What happened to all that other space? Is it normal to be missing that much usable space when setting up LUKS?

Thanks.

---

### Post by sleepycal on 2011-08-06
@bodhi.zazen Thank you very much for this guide. Although I didn't read much of the 'filler', I found the listing of correct commands in their correct order extremely helpful.

---

### Post by bodhi.zazen on 2011-08-06
> **sleepycal said:**
> @bodhi.zazen Thank you very much for this guide. Although I didn't read much of the 'filler', I found the listing of correct commands in their correct order extremely helpful.

You are most welcome. Rare to find someone who does not need a little of the background "filler" on these forums as LVM is not the default behavior in Ubuntu, but more power to you.

---

### Post by scarf on 2011-11-25
i am on the step 5 of the reduction part, with fdisk, and not sure what to do there.  my disk layout is a bit different with just two primary partitions.  i've already got my LVM shrunk to ~20G and i want to shrink the partition down to there also, basically where crypt now ends.  what is it i need to do in fdisk to shrink /dev/hda2 now?  thanks

here some info:
```
$ sudo fdisk -l

Disk /dev/hda: 40.0 GB, 40007761920 bytes
255 heads, 63 sectors/track, 4864 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x3f423f42

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1          31      248976   83  Linux
/dev/hda2              32        4864    38821072+  83  Linux

Disk /dev/dm-0: 39.7 GB, 39751725568 bytes
255 heads, 63 sectors/track, 4832 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

Disk /dev/dm-0 doesn't contain a valid partition table

Disk /dev/dm-1: 10.8 GB, 10850664448 bytes
255 heads, 63 sectors/track, 1319 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

Disk /dev/dm-1 doesn't contain a valid partition table

Disk /dev/dm-2: 536 MB, 536870912 bytes
255 heads, 63 sectors/track, 65 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

Disk /dev/dm-2 doesn't contain a valid partition table

$ sudo pvdisplay
  --- Physical volume ---
  PV Name               /dev/dm-0
  VG Name               graveyard
  PV Size               20.00 GB / not usable 3.81 MB
  Allocatable           NO
  PE Size (KByte)       4096
  Total PE              5119
  Free PE               2404
  Allocated PE          2715
  PV UUID               HMRsf8-1ePs-J33c-4tQu-7MtA-V6dv-O0U10R
$ sudo lvdisplay
  --- Logical volume ---
  LV Name                /dev/graveyard/root
  VG Name                graveyard
  LV UUID                C7bLop-WiHU-dwRy-3jBR-k1QP-rQEH-X9Zchr
  LV Write Access        read/write
  LV Status              available
  # open                 1
  LV Size                10.11 GB
  Current LE             2587
  Segments               1
  Allocation             inherit
  Read ahead sectors     auto
  - currently set to     256
  Block device           254:1

  --- Logical volume ---
  LV Name                /dev/graveyard/swap_1
  VG Name                graveyard
  LV UUID                yyUTnD-JVGR-BzVb-krSR-Mswq-aYoE-9YYfJt
  LV Write Access        read/write
  LV Status              available
  # open                 2
  LV Size                512.00 MB
  Current LE             128
  Segments               1
  Allocation             inherit
  Read ahead sectors     auto
  - currently set to     256
  Block device           254:2

```

---

