---
title: "Seriously impressed with Clonezilla - Just gotta say..."
date: 2011-06-17
forum: The Cafe
---

### Post by bluelamp999 on 2011-06-17
I've just used Clonezilla to image my dual booting (Win7/Ubuntu 10.10) 320 GB Samsung Spinpoint F4 to a shared drive on my home server.

I then clon(zilla)ed that image to a brand new Spinpoint F4.

It all worked perfectly and was dead easy.

As I say, I'm seriously impressed.

Kudos to Clonezilla.

Edit: Just donated a few bucks to Clonezilla

---

### Post by jeffathehutt on 2011-06-17
Clonezilla is an excellent program.  I used it once to directly clone everything from a dying hard drive to a new hard drive in the same computer.  Very easy to use and saved all the data from being lost. :)

---

### Post by handy on 2011-06-17
After dd failed, on my first attempt to upgrade the HDD in my 24" iMac, (everything was there but I could only boot into OSX, & could not get Arch to boot no matter what I tried!) I got around to having a try using Clonezilla which worked faultlessly to clone a 320GB drive to a 1.5TB drive with multiple partitions using the following file systems:

fat32
HFS+
Ext3
JFS

I may or may not have still been using /swap for Linux at that stage.

I pulled the drive out of the iMac, & stuck the two drives into my old Athlon machine where I used SATA -> IDE adapters, booted with the Clonezilla LiveCD & made sure I didn't stuff up my source & destination drives & away it went.

In a past life I was using Norton Ghost with images multiple times every week. If Clonezilla had of been around & as good as it was when I used it to benefit the iMac, I would have been using it instead as it is brilliant software that uses the appropriate tools to suit the job, including dd.

---

### Post by kherring7383 on 2011-06-18
I too totally agree, Clonezilla is perfect for cloning one drive to another. For a long time, I used Acronis to clone my Ubuntu drive. But when I started using clonezilla, I found it to be easier and faster. The best part, I didn't have to create a new drive UUID and a SWAP Partition.

---

### Post by Thewhistlingwind on 2011-06-18
The only disk cloning I've done was with dd.

---

### Post by timZZ on 2011-06-18
This was valuable thank you ... I going to try and use CloneZilla right now.

---

### Post by aysiu on 2011-06-18
> **Thewhistlingwind said:**
> The only disk cloning I've done was with dd.
Clonezilla is a lot faster.

Try Clonezilla-ing a 500 GB hard drive and then dd-ing the same. Clonezilla will win by hours.

Or, better yet, clone a 250 GB hard drive to a 1 TB drive using Clonezilla. Then try it with dd.

---

### Post by c-1000 on 2011-06-18
i am *wild* about clonezilla. 

i use it as a sort of "meta-os" -- there is a /clone partition on my disk, and i have a bunch of different distros and desktop environments that i can swap out in just a couple of minutes.
its invaluble when building up from a minimal install; almost like having a save point in a video game.
the only problem im running into is trying to manage all these clones! :p

im just now starting to scratch the surface on some of the more advanced features of this amazing piece of software.

---

### Post by FuturePilot on 2011-06-18
Until you try to put your image on a drive smaller than the original..

---

### Post by aysiu on 2011-06-18
> **FuturePilot said:**
> Until you try to put your image on a drive smaller than the original..
What cloning software would you recommend for that case?

---

### Post by sammiev on 2011-06-18
I have been using Clonezilla for over a year now and I must add that you can try almost anything as you know you can return it to what it was in 30 min or less. +1 for Clonezilla. GL :)

---

### Post by bluelamp999 on 2012-09-16
Update!

Just in case anyone's looking/interested...

I've just used Clonezilla to backup/restore a full clone of an NTFS formatted SSD.

Worked perfectly and alignment is identical

Before...
```
Description	Disk drive
Manufacturer	(Standard disk drives)
Model	M4-CT128M4SSD2 ATA Device
Bytes/Sector	512
Media Loaded	Yes
Media Type	Fixed hard disk
Partitions	1
SCSI Bus	0
SCSI Logical Unit	0
SCSI Port	0
SCSI Target ID	0
Sectors/Track	63
Size	119.24 GB (128,034,708,480 bytes)
Total Cylinders	15,566
Total Sectors	250,067,790
Total Tracks	3,969,330
Tracks/Cylinder	255

Partition	Disk #1, Partition #0
Partition Size	99.61 GB (106,954,752,000 bytes)
Partition Starting Offset	4,194,304 bytes

```


After...
```
Description	Disk drive
Manufacturer	(Standard disk drives)
Model	M4-CT128M4SSD2 ATA Device
Bytes/Sector	512
Media Loaded	Yes
Media Type	Fixed hard disk
Partitions	1
SCSI Bus	0
SCSI Logical Unit	0
SCSI Port	0
SCSI Target ID	0
Sectors/Track	63
Size	119.24 GB (128,034,708,480 bytes)
Total Cylinders	15,566
Total Sectors	250,067,790
Total Tracks	3,969,330
Tracks/Cylinder	255

Partition	Disk #1, Partition #0
Partition Size	99.61 GB (106,954,752,000 bytes)
Partition Starting Offset	4,194,304 bytes

```

Unless I was just lucky this proves to me that Clonezilla can handle the alignment for SSDs...

Hope this helps...

---

### Post by vexorian on 2012-09-16
I love cloneZilla. It is the perfect thing to install in your External hard drive and it surely beats the backup tools that come with them.

---

### Post by Porcini M. on 2012-09-19
This thread convinced me to give it a spin - I'm cloning my laptop HD now (posting from my work laptop). Really neat tool - easy to use, great concept (i.e. "cloning", and not having to worry about the details/complications of "copying").

---

### Post by meanmrmustard on 2012-09-26
This thread got me to give Clonzilla a try.
It was very fast although the cloned drive doesn't boot.
Not sure if I just need to install Grub2 or what.
Any advice?

---

### Post by vexorian on 2012-09-26
If you only cloned the partition and then restored the partition, then you might need to install grub2 in the MBR and tell it to use the partition.

If you cloned the whole HDD (and then restored it) then you should be able to boot it. But are you receiving an actual error message or something? Maybe the drive is booting but the OS is crashing. Also, if you move windows to another PC, chances are it won't boot at all.

---

### Post by meanmrmustard on 2012-09-26
> **vexorian said:**
> If you only cloned the partition and then restored the partition, then you might need to install grub2 in the MBR and tell it to use the partition.

If you cloned the whole HDD (and then restored it) then you should be able to boot it. But are you receiving an actual error message or something? Maybe the drive is booting but the OS is crashing. Also, if you move windows to another PC, chances are it won't boot at all.

I did clone and restore the partitions separately.
I'll try again and do the whole drive to see what happens.

This is a Lucid installation that I've customized for audio recording.
I could just re-install and build it all over again.
That's what I'll probably end up doing eventually since I'd like to switch to the 64 bit version.

---

### Post by Tac2 on 2012-09-27
Yes, Clonezilla is a great tool. The only issue I've had with it is that it doesn't work with RAID (at least some seamlessly). Otherwise it's perfect for quickly making a restorable image of a system. 

Now, if you need to move to a smaller drive as someone posted above, Clonezilla won't work. For this you can use a program like [fsarchiver]("http://www.fsarchiver.org/Main_Page"). fsarchiver basically takes all the contents of one or more partitions and puts it in an archive. You can then restore the filesystems onto the same or another disk using the archive. However, unlike with Clonezilla, you will have to create the partitions first. Also, I do not believe that fsarchiver saves info from the MBR. So cloning a system with fsarchiver will be a little more work than with Clonezilla, but it is the only way I know if you need to clone to a smaller disk.

The procedure with fsarchiver is something like this:

Lets say you have a 500 GB HDD in one system (OLD) and you want to clone it onto a 256 GB SSD in another system (NEW). OLD has 4 partitions: 
/dev/sda1 - 250 GB Windows XP partition (ntfs - 90 GB used)
/dev/sda2 - 50 GB Ubuntu root partition (ext4 - 25 GB used) 
/dev/sda3 - 196 GB data partition (ntfs - 80 GB used)
/dev/sda4 - 4 GB swap 

On NEW you want the following partitions:
/dev/sda1 - 50 GB Ubuntu root partition (ext4) 
/dev/sda2 - 100 GB Windows XP partition (ntfs)
/dev/sda3 - 102 GB data partition (ntfs)
/dev/sda4 - 4 GB swap 

You will need a LiveCD/USB with fsarchiver, such as SystemRescueCD. Download one and burn it to a CD or write it to a USB stick.
You will also need a USB harddrive (or some other external storage - can be NFS or SSH or Samba etc) for storing the backup archive.

First you need to create an archive with the partitions from OLD. 

1) Boot up SystemRescueCD and get to the command line. 
2) Mount your external storage, for example in /mnt/storage
2) Create an archive with all the partitions (except swap) using the command: 

```
fsarchiver savefs /mnt/storage/backup.fsa /dev/sda1 /dev/sda2 /dev/sda3 
```

Now go to the NEW system:

1) First you need to create the partitions. You can use a command line program like fdisk, gdisk or parted, or a GUI program like GParted. All of those are on SystemRescueCD. So boot up the system with SystemRescueCD and use your preferred tool to create the partitions on NEW (Note: you don't need to put filesystems on them, fsarchiver can handle that).
2) Get to command line, and make sure your remote storage is mounted (e.g. at /mnt/storage). 
3) Restore the partitions using the following command:

```
fsarchiver restfs /mnt/storage/backup.fsa id=1,dest=/dev/sda1 id=0,dest=/dev/sda2 id=2,dest=/dev/sda3
```

(Notice that I swapped the Windows and Ubuntu partitions around. To find out what ID the partitions have in the archive, use the command: fsarchiver archinfo /mnt/storage/backup.fsa)

4) Now you can chroot into /dev/sda1 and write GRUB2 to MBR. Before chroot'ing into /dev/sda1 and installing GRUB2, you first need to bind-mount /dev, /dev/pts, /proc and /sys, like so:

```
mkdir /mnt/ubuntu
mount /dev/sda1 /mnt/ubuntu
mount --bind /dev /mnt/ubuntu/dev
mount --bind /dev/pts /mnt/ubuntu/dev/pts
mount --bind /proc /mnt/ubuntu/proc
mount --bind /sys /mnt/ubuntu/sys

```

Then you can chroot into /dev/sda1 and write GRUB2 to MBR:

```
chroot /mnt/ubuntu
grub-install /dev/sda
update-grub
```

Now you can reboot, remove the LiveCD/USB and boot into your freshly cloned system.

(Wow I see that turned into a small guide, heh. Well, just wanted to illustrate how it would work with fsarchiver. Personally I like it a lot, especially for making archives of LVM snapshots.)

---

### Post by leclerc65 on 2012-09-27
My HDD looks like this

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048    81922047    40960000    7  HPFS/NTFS/exFAT
/dev/sda2        81922048   184322047    51200000    7  HPFS/NTFS/exFAT
/dev/sda3       184322048   430082047   122880000    7  HPFS/NTFS/exFAT
/dev/sda4       430082048   488396799    29157376    5  Extended
/dev/sda5       430084096   482252799    26084352   83  Linux
/dev/sda6       482254848   488396799     3070976   82  Linux swap / Solaris

I have XP in SDA1, Windows 7 in SDA2, Linux in SDA5. I can clone SDA1, SDA2 in one run, SDA5 in another but if I try to clone the whole disk, Clonezilla will blow up. Space is not a problem, my external 500G USB HDD is half empty, also partition SDA3 is almost empty. Any idea ?

---

### Post by Sef on 2012-09-27
Clonezilla works great. I have used it to back up my hard drive. Sigh, I am overdue with the latest back up.

---

### Post by Tac2 on 2012-09-27
> **leclerc65 said:**
> My HDD looks like this

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048    81922047    40960000    7  HPFS/NTFS/exFAT
/dev/sda2        81922048   184322047    51200000    7  HPFS/NTFS/exFAT
/dev/sda3       184322048   430082047   122880000    7  HPFS/NTFS/exFAT
/dev/sda4       430082048   488396799    29157376    5  Extended
/dev/sda5       430084096   482252799    26084352   83  Linux
/dev/sda6       482254848   488396799     3070976   82  Linux swap / Solaris

I have XP in SDA1, Windows 7 in SDA2, Linux in SDA5. I can clone SDA1, SDA2 in one run, SDA5 in another but if I try to clone the whole disk, Clonezilla will blow up. Space is not a problem, my external 500G USB HDD is half empty, also partition SDA3 is almost empty. Any idea ?

How does it blow up? Does it return an error, freeze, restart, what happens?

---

### Post by markp1989 on 2012-09-27
I was using clonezilla at work the other day, was setting up 10 identical machines for an event, I installed and configured the first machine as I wanted but didnt activate any of the licence keys. took an image of that 1 machine using the PXE boot from our clonezilla server and deployed it on the other 9 machines.  I had to manually enter the product keys on each machine after wards.

enabled my to have 10 machines set up running their own genuin version of windows (each one with its own licence)  with all the software and drivers I needed in half an afternoon, if I had installed each of those machines manually it would have taken me a lot longer than that, proper impressed.

---

### Post by leclerc65 on 2012-09-27
> **Tac2 said:**
> How does it blow up? Does it return an error, freeze, restart, what happens?
It finishes cloning the SDA1, then freezes with a dump. I cannot copy/take a screen shot. Before turning off the computer I try to copy the last 3 lines which look like the following:

947.160676 Code: 8b 56 .... (bunches of hex numbers)
947.160790 EIP: [<c10da>]_pollwait + 0x5e/0xaa SS:ESP 0068 ecl25bbbd0
947.160801 CR2: 0000000076d458c0

---

