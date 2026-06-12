---
title: "btrfs would not install on USB hard drive"
date: 2013-06-07
forum: Ubuntu Development Version
---

### Post by jerrylamos on 2013-06-07
I've got 4 partitions on USB SSD formated ext4, saucy, ringtail, library.  I tried to install saucy onto one of the partitions specifying btrfs.  Refused to format.  Hung ubiquity.  Same result with ringtail.  Subsequent ext4 installed fine.

I poked around internet to find out what restrictions btrfs might have and didn't see anything relevant.  I have installed saucy btrfs on SSD installed hard drive alongside ext4 partitions O.K.

Any pointers on what should/shouldn't work, and what about a mix of ext4 and btrfs which is what I have on the installed drive?

Thanks.

---

### Post by grahammechanical on 2013-06-07
Where some of my attempts to install Ubuntu on btrfs have failed is at the point that Ubiquity tries to install Grub into the MBR. I recently had ubiquity stop the install because there was not enough space on the partition. Stopped at copying files. There was 10GB and the second attempt worked. You may need either a small boot partition or at least 1MiB of unallocated space before the first partition.

If you do get saucy installed on btrfs then it will appear in the Grub menu but if you run update-grub and grub-install from the raring partition it will not detect the btrfs installation of Ubuntu. Grub does not detect more than one btrfs Ubuntu install and it does not detect btrfs Ubuntu on another hard disk. This is my recent experience.

I at present have raring+Ext4 and saucy+btrfs and they are running without problems, except the usual stuff we get with Ubuntu+1. On another hard disk I have a mixture of 12.04, 12.10, 13.04, 13.10. Two are btrfs and the rest are Ext4. Apart from being unable to see the btrfs installs in Grub, I do not have any issues with mixing them up.

I do not have a lot of confidence in the recent saucy iso images.

---

### Post by jerrylamos on 2013-06-07
Grahammechanical, thank.  That's just the info I needed.  My take, the ubuntu/btrfs implementation is half baked at the moment.  This is a U+1 unstable forum.  Any clue where Ubuntu is headed on disk formats?

Thanks much.

---

### Post by grahammechanical on 2013-06-08
I am guessing that the devs are slightly distracted at the moment. Before btrfs becomes the default file system there needs to be a GUI snapshot manager for the ordinary user. I think that for the user of a single machine with one installation of Ubuntu then btrfs will not prove to be much of a problem. Things get tricky for the tester with multiple installs. I also think that btrfs would be great for using the development branch. Have the ability to rollback after an update would be great. A GUI snapshot manager would be useful there as well.

Ventrical has proved that with btrfs we can revert a distribution upgrade. It is ordinary users that would want to do this but a GUI snapshot manager would be needed for the ordinary user to benefit from it. This where I see things standing. These are not impossible tasks to put right but I cannot see time and effort being used for this at this time. So, I am not confident in seeing btrfs become the default by 14.04.

Regards.

---

### Post by ventrical on 2013-06-08
@grahammechanical

Ditto.  Most of the resources are going into Next, Unity 8 , mir (who knows) Steam (whew!)  and a thousands of bugs and interfected depends. I am going to keep checking it out.

@jerrylamos

 Two earlier attempts  at install brtfs on USB stick failed here also. I think it has to do with Copy on Write  technolgy and the way it is wired to hdds.

 I'll keep trying though.. Just been busy again ...

---

### Post by ventrical on 2013-06-23
Just no luck at all  getting this task done. Grub will just not load on the btrfs formated USB.

hmmmm..

---

### Post by grahammechanical on 2013-06-24
I am still recovering from the emotional trauma of the last collapse of my btrfs pack of cards. I messed up big time. I had the brilliant idea of putting precise on btrfs and then upgrading all the way through to saucy, taking snapshots as I went. I thought that I would then be able bring up any one of the 4 versions for testing without needing to install any other them.

The upgrade to Quantal broke the desktop. I tried to roll back to precise using a live session. All went fine but I forgot to run update-grub so I got grub rescue. I corrected that using boot repair and failed to notice that it would grub-install into the MBR of both my hard disks. So, I was back to the old 1.99 grub on both disks. What a sorry looking mess but worse of all none of my 3 btrfs installs was in either of the menus. This was especially painful as what I consider as my rolling development release was saucy on btrfs on sdb8 and I could not load it.

Solution? Boot into raring on sdb1; run grub-install MBR sdb; create a custom grub file (15_custom) using the lines from saucy (sdb8) grub.cfg. Run update-grub. Now I had saucy sdb8 btrfs in a grub menu and could boot into it. I have since run grub-install sdb from saucy sdb8 btrfs and modified 15_custom to show all my btrfs installs.

If this looks confusing to you. Think of me trying to sort out this mess. Grub os-prober is the culprit.

In case you do not know, update-grub puts its nose into the files in /etc/grub.d and creates the menu from stuff found there. We can use the 40_custom file to create our own configuration file but we must save it with a new name.
 
The entries in 06_custom would go at the top of the menu and 15_custom would come after the line pointing to the kernel on the active partition. So, by calling the file 15_custom I still keep my active partition at the top of the menu.

I found it more accurate to copy and paste the relevant lines from grub.cfg rather trying to type things in myself.

Regards.

@ventrical

A question. Does a USB memory stick/disk have an MBR? I know it is possible to install grub to the so-called MBR  of a external USB drive but where does it go? Is it like installing grub into a partition? Do we need a small non btrfs partition on a USB stick/drive? That's more than one question. Sorry. I think that you are doing relevant research because very large USB drives are becoming common. Sooner or later some person is going to think of the benefits of btrfs for large data collections and want to use it.

---

### Post by grahammechanical on 2013-06-24
@ventrical

I found this comment

> [COLOR=#000000]*The "preserving /home" feature appears to be incompatible with btfs filesystems, although you shouldn't be using btfs because it's not stable yet. I still didn't lose any data, the installer just refused to continue.[/COLOR]

in this thread

[http://ubuntuforums.org/showthread.php?t=2157047](http://ubuntuforums.org/showthread.php?t=2157047)

It is about doing a re-install over an existing Ubuntu with combined /home partition and without formatting. I wonder if the real issue is the failure to install Grub into the MBR? Another area to test?

Regards.

---

### Post by jerrylamos on 2013-06-24
Does a USB drive have an MBR?  How do I tell - here's what parted says
```
(parted) print all
Model: ATA Hitachi HTS54502 (scsi)
Disk /dev/sda: 250GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type      File system     Flags
 1      1049kB  14.0GB  14.0GB  primary   ntfs            diag
 2      14.0GB  14.1GB  105MB   primary   ntfs            boot
 3      14.1GB  124GB   110GB   primary   ntfs
 4      124GB   250GB   126GB   extended
 5      124GB   135GB   10.5GB  logical   ext3
 6      135GB   136GB   1049MB  logical   linux-swap(v1)
 7      136GB   146GB   10.5GB  logical   ext4
 8      146GB   147GB   1049MB  logical   ext3
 9      147GB   148GB   1049MB  logical   ext2
10      148GB   190GB   41.9GB  logical   ext3
11      190GB   201GB   10.5GB  logical   ext4
12      201GB   250GB   49.3GB  logical   ext2


Model: INTEL SS DSA2M080G2GN (scsi)
Disk /dev/sdb: 80.0GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type      File system  Flags
 1      1049kB  10.5GB  10.5GB  primary   ext4         boot
 2      10.5GB  21.0GB  10.5GB  primary   ext4
 3      21.0GB  31.5GB  10.5GB  primary   ext4
 4      31.5GB  80.0GB  48.6GB  extended
 5      31.5GB  41.9GB  10.5GB  logical   ext4
 6      41.9GB  80.0GB  38.1GB  logical   ext3
```
This is a netbook with Windows 7 and a number of ubuntu's on the built in sda.  the USB is sdb.

---

### Post by grahammechanical on 2013-06-25
@jerrylamos

I must have been almost brain-dead when I asked about USB MBR. I think a USB hard disk is a standard hard disk with a USB interface to the motherboard. So, it would have a normal MBR. And as I think about it Solid State Disks (SSD) must also have a place for the boot system (MBR/EFI) otherwise we could not install onto them. I am just not sure about USB memory sticks. And yet it is possible to install Grub onto an USB stick. Just not on btrfs, it seems.

Please disregard my befuddled musings.

---

### Post by The Cog on 2013-06-25
USB memory sticks generally have an MBR just the same as ordinary hard disks. In this case, you have sdb1, sdb2 etc.

But it is possible to format a USB stick raw: mkfs.vfat /dev/sdb and it mounts just as a partition would. I think windows users wouldn't see any difference. Not sure what happens under Linux, and I don't have a spare to experiment with about my person. But I have used non-mbr sticks in the past.

---

### Post by ventrical on 2013-06-25
> **grahammechanical said:**
> 

@ventrical

A question. Does a USB memory stick/disk have an MBR? I know it is possible to install grub to the so-called MBR  of a external USB drive but where does it go? Is it like installing grub into a partition? Do we need a small non btrfs partition on a USB stick/drive? That's more than one question. Sorry. I think that you are doing relevant research because very large USB drives are becoming common. Sooner or later some person is going to think of the benefits of btrfs for large data collections and want to use it.

 I must confess that my last attempt was nothing but lame. I used this 32GB new ver 3.0 USB  Flash Drive but it has a firmware widget in it. I tried to erase it. It is 1kb big . geesh .. but Iv'e not given up!! Iv'e been up to my elbows with the funky broadcom blacklists that has really pi$$ed me off on some production machines.

 Anyways .. first things first .. i am going to take one of my persistent installs and  try to convert it to btrfs. The best usb flash to use is Dane brand. Eveything else (kingston especially) is no match .

---

### Post by ventrical on 2013-06-25
> **grahammechanical said:**
> @ventrical

I found this comment



in this thread

[http://ubuntuforums.org/showthread.php?t=2157047](http://ubuntuforums.org/showthread.php?t=2157047)

It is about doing a re-install over an existing Ubuntu with combined /home partition and without formatting. I wonder if the real issue is the failure to install Grub into the MBR? Another area to test?

Regards.

Thanks .. I'm just getting to it now.

That [http://ubuntuforums.org/showthread.php?t=2152412&p=12704390#post12704390](http://ubuntuforums.org/showthread.php?t=2152412&p=12704390#post12704390)  was a brilliant essay btw:)

---

### Post by grahammechanical on 2013-06-25
I have just tried re-install saucy+btrfs without re-formatting the partition.

First attempt=failure. Ubiquity crashed oh so nicely as it was part way through the installing system section.

Second attempt=success. The difference? In the first attempt i run Ubiquity from the Try + Install Ubuntu text mode screen. In the second attempt I ran it from a live desktop session.

I did notice one thing strange. During the second attempt I was used for user details, as normal. But I cannot remember being asked for those details during the first attempt. The installer went from the partitioner to copying files without wanting user details. I am sure of this.

Anyway even though this was the latest saucy daily build a reboot did not get me to the log in screen. So, I install saucy on Ext4 and it rebooted without any hassle. I am beginning to lose my faith in the marriage of saucy and btrfs. Too late for a divorce?

Regards.

---

### Post by ventrical on 2013-06-25
I have a current install in progress going on  with a 16GB USB flash drive.  I took the harddrive out and decided to burn a DVD and boot from there. I made 1 -1mb partition (logical) and a 2 GB ext4 (logical) . The rest for btrfs on raring. If that boots up and works then I'll see if I can grab other snapshots from other machines. Also upgrade to saucy and see what happens !

---

### Post by ventrical on 2013-06-25
> **grahammechanical said:**
> I have just tried re-install saucy+btrfs without re-formatting the partition.

First attempt=failure. Ubiquity crashed oh so nicely as it was part way through the installing system section.

Second attempt=success. The difference? In the first attempt i run Ubiquity from the Try + Install Ubuntu text mode screen. In the second attempt I ran it from a live desktop session.



This has been going on since Oneric. Actually , the case used to be that you had to use the SDC from the icon in the Unity Panel. That was the only way to get it to work. Looks like Ubiquity has regressed backwards once again.

---

### Post by ventrical on 2013-06-25
> **grahammechanical said:**
> @jerrylamos

I must have been almost brain-dead when I asked about USB MBR. I think a USB hard disk is a standard hard disk with a USB interface to the motherboard. So, it would have a normal MBR. And as I think about it Solid State Disks (SSD) must also have a place for the boot system (MBR/EFI) otherwise we could not install onto them. I am just not sure about USB memory sticks. And yet it is possible to install Grub onto an USB stick. Just not on btrfs, it seems.

Please disregard my befuddled musings.

Success here !!

  I have successfully installed (the raring final) with the btrfs format on a USB flash drive (Dane Brand-16GB). It is very , very slow but it boots up to lighdm, log on and then Unity 3d is there .. etc.. 

What I did.

Acer Extensa 4420 AMD dual core.

Remove SATA hard drive.

Burn raring-desktop-i386.iso to DVD using Brasero.

Set PC to boot from DVD/CD drive.

Insert DVD and USB flash memory stick.

Choose 'Install Ubuntu' from Ubiquity.

When partitioning options come up choose 'Something Else'

Erase all partitons.

Make a 1mb ext4 "Logical" partion.

Next, make a "Primary" btrfs partition (but leave about 2 GBs for the third partion.) Mark the primary btrfs  partion as  /  root.

Ignore messages about  ext4 partitons not having any designations.

Ignore messages about swapspace. (do not make a swapspace partion IMHO)

<continue> install

  After the install is complete it is buisness as usual. The only caveat is that btrfs is very , very slow on USB flash drives so wait, wait , wait for the 'Error sparse , press any key to continue'. It will boot up. I have run into a bug already from firefox (script error) so try these methods at your own risk.

edit:

The logic why.

My theory is that the physical hard drive has to be out and the network to the USB flash Drive has to be clean. Using the DVD/CD drive somehow tricks ubuntu partitoning/install tools to actually think that the USB flash drive is a physical HDD because the network path/s to the USB are clear.  I have tired this with many formats and I have found it always best to remove the hdd. Also .. There could be a bug from USB to USB install because there may be some noise on that network preventing the btrfs from installing on USB flash memory sticks.

my 2 cents worth.

---

### Post by ventrical on 2013-06-25
Here are some interesting screenshots from that install.

---

### Post by ventrical on 2013-06-25
@grahammechcanical

Notice that 1% of 1 MB being used?

---

### Post by ventrical on 2013-06-25
Here we go attemtping to take a snapshot and then trying to move it to another btrfs system.

```

ventrical@ventrical-Extensa-4420:~$ sudo apt-get install apt-btrfs-snapshot
[sudo] password for ventrical: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  apt-btrfs-snapshot
0 upgraded, 1 newly installed, 0 to remove and 313 not upgraded.
Need to get 7,852 B of archives.
After this operation, 97.3 kB of additional disk space will be used.
Get:1 http://ca.archive.ubuntu.com/ubuntu/ raring/universe apt-btrfs-snapshot all 0.3.4.1 [7,852 B]
Fetched 7,852 B in 0s (28.4 kB/s)             
Selecting previously unselected package apt-btrfs-snapshot.
(Reading database ... 154648 files and directories currently installed.)
Unpacking apt-btrfs-snapshot (from .../apt-btrfs-snapshot_0.3.4.1_all.deb) ...
Setting up apt-btrfs-snapshot (0.3.4.1) ...
ventrical@ventrical-Extensa-4420:~$ sudo -i
root@ventrical-Extensa-4420:~# apt-btrfs-snapshot supported
Supported
root@ventrical-Extensa-4420:~# 


```

```

root@ventrical-Extensa-4420:~# sudo apt-get install htop
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  htop
0 upgraded, 1 newly installed, 0 to remove and 313 not upgraded.
Need to get 67.7 kB of archives.
After this operation, 189 kB of additional disk space will be used.
Get:1 http://ca.archive.ubuntu.com/ubuntu/ raring/universe htop i386 1.0.2-1 [67.7 kB]
Fetched 67.7 kB in 0s (185 kB/s)
Supported
Create a snapshot of '/tmp/apt-btrfs-snapshot-mp-5vmxan/@' in '/tmp/apt-btrfs-snapshot-mp-5vmxan/@apt-snapshot-2013-06-25_16:00:22'
Selecting previously unselected package htop.
(Reading database ... 154660 files and directories currently installed.)
Unpacking htop (from .../archives/htop_1.0.2-1_i386.deb) ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf-2.index...
Processing triggers for desktop-file-utils ...
Processing triggers for gnome-menus ...
Processing triggers for man-db ...
Setting up htop (1.0.2-1) ...
root@ventrical-Extensa-4420:~# 

```

---

### Post by ventrical on 2013-06-25
I cannot move one snapshot to another system.

Any suggestions?

eddit:

Or .. how do I enable user sharing ?

---

### Post by grahammechanical on 2013-06-25
May I make an obvious but easily forgotten suggestion? You may have not forgotten at all but did you make the folder and all that is in it read/write by all?

I use gksudo nautilus and then change the permissions to the folders. I had to do this when I put in this second hard drive that I was going to use mainly as a data partition. Once I copied the folders from my old HD over to the new drive I had to change the permissions before I could write to any of the documents from another partition.

Well, I confirmed that Ubiquity fails to re-install Ubuntu on a btrfs partition unless the partition is formatted as part of the re-install. Ubiquity does not ask for the user details unless the partition is marked to be formatted. It then crashes at the point of creating user. So, I guess that Ubiquity is not so good at reading btrfs partitions. Just like grub os-prober.

I have also noticed that the partitioner recognises that a partition is a btrfs type but it does not know how much space is used (unknown).

And so we live.

---

### Post by ventrical on 2013-06-25
> **grahammechanical said:**
> May I make an obvious but easily forgotten suggestion? You may have not forgotten at all but did you make the folder and all that is in it read/write by all?



Tried samba and it is not being too friendly at all.

---

### Post by ventrical on 2013-06-25
> **ventrical said:**
> Tried samba and it is not being too friendly at all.


Edit:

 I think I really messed it up by not setting the shares. Lots to learn..;) I was at least able to change the name .

---

### Post by ventrical on 2013-06-26
> **grahammechanical said:**
> May I make an obvious but easily forgotten suggestion? You may have not forgotten at all but did you make the folder and all that is in it read/write by all?


@graham,

 I got about  this "" close to copying the @snapshot file .. but I keep getting errors with special files. There is something I am not doing right here with permission settings. All seems to go well when all of a sudden I get the error "can't copy special file" which is part of the @apt-snapshot folder. Perhaps this file  has a locked in format that will not allow for compression or moving/copying.  I even set the smb.conf file in [global settings] to allow .

 I don't know .. any strings you know off hand ?

---

### Post by ventrical on 2013-07-03
> **ventrical said:**
> I must confess that my last attempt was nothing but lame. I used this 32GB new ver 3.0 USB  Flash Drive but it has a firmware widget in it. I tried to erase it. It is 1kb big . geesh .. but Iv'e not given up!! Iv'e been up to my elbows with the funky broadcom blacklists that has really pi$$ed me off on some production machines.

 Anyways .. first things first .. i am going to take one of my persistent installs and  try to convert it to btrfs. The best usb flash to use is Dane brand. Eveything else (kingston especially) is no match .


  I just wanted to append this message and do some house keeping. I had aquired a Transcend 32 GB USB  Flash Drive ver 3.0.  It is backwards compatible and runs on Ver 2.0 and makes it appear that all my old PCs have the speed of a Quad core.!! I put Ubuntu on it and it is  4 times faster that my WD 1.5 TB SATA II.

 just saying  ...:)

awesome time saver...

---

