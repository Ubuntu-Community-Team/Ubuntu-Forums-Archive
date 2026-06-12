---
title: "Ubuntu for newbies"
date: 2005-05-06
forum: The Cafe
---

### Post by tbresson on 2005-05-06
I want to install Ubuntu on my server and delete the existing Windows which is on it right now, but.. I want everything to work the first time, and that's perhaps quite a bit to expect when your a newbie and when to run Linux.

As a precaution I decided to pull out one of my old P3 933 mhz Dell desktop machines and install linux distros on it like never before just to get the experience, and this is where I decided Ubuntu should be my distro of choice (yay!  O:) )

Things are going okay as is, I have a few things I need the OS to do for me which I'm practising setting up, e.g. Samba, VNC etc. - later on I'll try with an FTP server too, but in general I'm hoping to replace Windows.

I'm writing here because there might be people out there who have done the same, want to do the same, or perhaps are planning on doing the same, and I might get some good ideas, hints og tricks by writing here.

This is the solution I'm hoping for:

- A fileserver (I have 2 IDE controllers, 1 on-board and 1 Promise TX2-100, and 6 IDE disks, and my client (other PC) is a WinXP PC).

- A GUI (I want to use my computer for web browsing (Firefox, of course  ;-)  and also for burning CDs/DVDs (I havn't even tried out any software yet and doesn't know what it's called

- A Remote administration possibility (I want to remote my machine if I have too, who doesn't? VNC was a obvious solution and I got it to work though I've seen better software on Windows, but then again not for free :P)

Problems:
I expect to fall into some problems with this, perhaps with the many disks and the IDE controllers, also I have to convert the filesystem on the disks fra NTFS (perhaps format) - which app is used for that?

Also I suspect that samba running on different disks might be an issue - anyone know about this? e.g. on Windows I have c: d: e: f: g: h: as IDE disks, but on my test machine I only have 1 disk (no room for more) - so I get "Filesystem" in the file browser. How does it look with more disks? 

I might have forgotten a few things in here, since there's so much to consider before taking down a machine from the network and installing a different kind of OS on it. But I'm looking forward to it, and I hope by writing here others might get help too  :grin: 

So any helpful comments, suggestions or likewize are appreciated  O:)

---

### Post by fng on 2005-05-06
- cd burning software : try gnomebaker, graveman or k3b in the ubuntu repositories. Myself, i use gnomebaker.

- multiple disks : Handling multiple disk is totaly different than in windows.  You have 1 virtual filesystem and all your disks/partitions are mounted in this filesystem in a directory you choose.

i also have 3 hd's and I mounted them (d: and e: in windows) respectivly  in /home/your_user/movies, /home/your_user/music.  My so called c: drive has the root filesystem on it.

to mount drives in the filesystem use the mount command:
sudo mount -t ntfs /dev/hdxx /directory/you/mount/them/on 

The first x in hdxx stands for the drive number
c: is hdax
d: is hdbx 
etc...
(if you only had 1 partition/drive in windows :) )

The second x in hdxx stands for the partition number on the drive
hda1 = partition number 1 on the first physical drive

To see a list of available partitions to mount, type 'ls /dev/hd*' in a terminal

---

### Post by tbresson on 2005-05-06
Thanks for the info :o) Although I do have some other questions :P

1) Is there a way to mount the disks at startup automatically? (do a need an equvilant autoexec.bat or something?) Also the -t ntfs parameter you wrote, that will only work as read only since it's NTFS right? should I use EXT3 or ReiserFS for my additional disks (not the system disk) if possible?

2) Is there a GUI interface for disk partitioning, e.g. Disk Manager or should I use fdisk or diskdruid (I think it's called) or something similar text-based partitioner?

---

### Post by fng on 2005-05-06
yes you can mount them at starup

You need to edit the following file with your favorite editor : /etc/fstab
sudo nano /etc/fstab

It probably looks something like this :
```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda2       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda1       none            swap    sw              0       0
/dev/hdc1       /home/fng/movies        reiserfs defaults       0       2
/dev/hdd1       /home/fng/music        reiserfs defaults       0       2
/dev/hdb        /media/cdrom0   udf,iso9660 ro,user,noauto  0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

```

You see these 2 lines?

```

/dev/hdc1       /home/fng/movies        reiserfs defaults       0       2
/dev/hdd1       /home/fng/music        reiserfs defaults       0       2
```

Those are the lines to automount my other drives at startup.
You probably have to change reiserfs to ntfs for your setup at home.

Dont know about the gui interface for disk partitioning, i use fdisk myself.  
Don't fear the command line, embrace it, because its very powerful when you got to know it.

---

### Post by &#12465;&#12452;&#12488; on 2005-05-06
If you want a GUI for partitioning, GParted would be a good choice.
Open a terminal, and enter:
```
sudo apt-get install gparted
```
This will install install a program for easy, graphical partitioning, just like PartitionMagic on Windows.

---

### Post by tbresson on 2005-05-10
Nice! I will try that out  :)

---

### Post by Alexander Kirillov on 2005-05-10
[QUOTE=tbresson]
I expect to fall into some problems with this, perhaps with the many disks and the IDE controllers, also I have to convert the filesystem on the disks fra NTFS (perhaps format) - which app is used for that?
[/QUOTE]

NTFS filesystem can be read but not written to in Ubuntu (and Linux in general). So you will have to reformat it - probably to FAT32. You can do it during install or later, using "parted" command line  tool or gparted. 

 Warning: this erases all data! If you have files you wnat to keep, copy them to a different partition first, then copy back.

---

### Post by tbresson on 2005-05-19
I finally got the system installed .. I run a dual boot right now and I havn't configured anything yet on the running system.

But I found this piece of information helpful for myself so I though I'd just post it here   :) 

To get Gnomebaker to work add this: 
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary universe multiverse

to this file:
/etc/apt/sources.list

and do this in console afterwards:
apt-get update 

After this both the Gnomebaker and the gparted is visible in the Synaptic system :) (and available via apt-get)

---

### Post by poofyhairguy on 2005-05-19
welcome

---

### Post by tbresson on 2005-06-27
Well.. I finally got the time to really play with my new system and I found out a couple of new things which I have issues with ...

Apparently I have a network driver issue which I posted here:
[http://ubuntuforums.org/showthread.php?p=230431](http://ubuntuforums.org/showthread.php?p=230431)

And also a little samba issue:
[http://www.ubuntuforums.org/showthread.php?p=230441](http://www.ubuntuforums.org/showthread.php?p=230441)

I hope someone can help me with this...

---

