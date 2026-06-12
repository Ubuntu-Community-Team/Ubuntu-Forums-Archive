---
title: "daru3 Xubuntu Install"
date: 2009-09-26
forum: System76 Support
---

### Post by AlexInBlack on 2009-09-26
For some reason, it seems that Xubuntu will never work stably on my daru3.
I seem to always crash and get some fatal filesystem errors/corrupted blocks that I can never find out how to fix using Google/Ubuntu forums. To date, since I've got the laptop about 3 months ago, I've reinstalled Xubuntu at least 3 times because I couldn't figure out a way to fix my install.

I've been using Xubuntu 9.04 (amd64) installed via LiveUSB. I'm pretty sure it's not a problem with the LiveUSB OS (although it never starts up with X, as in I have to type "startx" every time I boot it up), since I've used the same LiveUSB OS to install Xubuntu on my desktop, which has yet to fatally crash/corrupt filesystems in a way I can't fix.
I'm also pretty sure my hard drive works because I can access my /home and Windows partitions.

Right now, boot-up fails and I get a message after "Loading, please wait..." that says: "Gave up waiting for root device." It then lists common problems. After that, I get: "ALERT! /dev/disk/by-uuid/f8acb85f-d1d3-4e8a-8cf3-80de0db403e0 does not exist. Dropping to a shell!" I then get dropped into BusyBox/initramfs.
I've tried mounting my / partition via a LiveUSB OS, but even with "sudo mount /dev/sda6 /media/jaunty -t ext3", I get the message about, "wrong fs type, bad option, bad superblock on /dev/sda6, missing codepage or helper program, or other error"
When I try "dmesg | tail" as suggested, I get "VFS: Can't find ext3 filesystem on dev sda6" among other messages.
This all happened on my second reboot after Firefox crashed and I had to press the power button to exit. The mouse cursor was stuck on the loading symbol. Switching to other workspaces via Ctrl-Esc or Ctrl-Alt-F# didn't work. Neither did using SysRq and pressing R S E I U B as I usually do when nothing else works. (I'm following the tips here: [http://www.brunolinux.com/01-First_Things_To_Know/Run-Away_Processes.html](http://www.brunolinux.com/01-First_Things_To_Know/Run-Away_Processes.html) and [http://www.brunolinux.com/01-First_Things_To_Know/Skinny_Elephants.html](http://www.brunolinux.com/01-First_Things_To_Know/Skinny_Elephants.html)).

Should I just try using a normal gnome install of Ubuntu on my daru3 or is there possibly something I'm doing wrong? (I make sure to install the System76 drivers as soon as the slew of updates are done after a fresh install).

---

### Post by thomasaaron on 2009-09-28
System76 doesn't support Xubuntu. JDB may have some tips for you. However...
> "sudo mount /dev/sda6 /media/jaunty -t ext3", I get the message about, "wrong fs type, bad option, bad superblock on /dev/sda6, missing codepage or helper program, or other error"
When I try "dmesg | tail" as suggested, I get "VFS: Can't find ext3 filesystem on dev sda6" among other messages.
...makes me wonder if you installed using the ext4 filesystem, which is still considered unstable. If so, you might want to try using ext3.

---

### Post by Eldera on 2009-09-28
There was a typo in post 2, which has been fixed. "System76 doesn't support Ubuntu." instead of "System76 doesn't support Xubuntu."

---

### Post by jdb on 2009-09-28
> **thomasaaron said:**
> System76 doesn't support Ubuntu. JDB may have some tips for you. However...

...makes me wonder if you installed using the ext4 filesystem, which is still considered unstable. If so, you might want to try using ext3.

I think Thomasaaron has hit the nail on the head.
It's probably trying to mount an ext3 partition because that is what /etc/fstab claims it to be.
The error says it is not an ext3 partition.

Can you boot to a live CD & post the output of:

```
parted -l
```


jdb

---

### Post by thomasaaron on 2009-09-28
Yes, I meant Xubuntu. Fixed it. Thanks.

---

### Post by AlexInBlack on 2009-09-29
parted -l only gives info about my LiveUSB OS.
Output:
Model: BUFFALO USB Flash Disk (scsi)
Disk /dev/sdb: 2064MB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
 1      32.3kB  2056MB  2056MB  primary  fat16        boot 

I'm pretty sure I formatted my / partition as ext3. GParted now says that the partition has an unknown filesystem. My Windows XP ext2/3 driver used to work for the partition too, but now shows it as raw. (It also showed my /home partition as raw after the Xubuntu crash before I booted my LiveUSB OS, mounted the /home partition, and offloaded some data.)

---

### Post by jdb on 2009-09-29
> **AlexInBlack said:**
> parted -l only gives info about my LiveUSB OS.
Output:
Model: BUFFALO USB Flash Disk (scsi)
Disk /dev/sdb: 2064MB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
 1      32.3kB  2056MB  2056MB  primary  fat16        boot 

I'm pretty sure I formatted my / partition as ext3. GParted now says that the partition has an unknown filesystem. My Windows XP ext2/3 driver used to work for the partition too, but now shows it as raw. (It also showed my /home partition as raw after the Xubuntu crash before I booted my LiveUSB OS, mounted the /home partition, and offloaded some data.)

I'm sorry, you need to run it as root:

```
sudo parted -l
```

I'm booted to a live CD right now & this is what I got:

```
ubuntu@ubuntu:~$ sudo parted -l
Model: ATA WDC WD1600AAJB-0 (scsi)
Disk /dev/sda: 160GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type      File system  Flags
 1      32.3kB  10.6GB  10.6GB  primary   ext3         boot 
 2      10.6GB  160GB   149GB   extended                    
 5      10.6GB  21.1GB  10.4GB  logical   ext3              
11      21.1GB  21.6GB  526MB   logical   ext3              
 8      21.6GB  32.3GB  10.7GB  logical                     
10      32.3GB  42.9GB  10.7GB  logical                     
 6      42.9GB  82.8GB  39.9GB  logical                     
 9      82.8GB  155GB   71.8GB  logical                     
 7      155GB   160GB   5429MB  logical                     


Model: ATA SAMSUNG SP2504C (scsi)
Disk /dev/sdb: 250GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type      File system  Flags
 1      32.3kB  21.0GB  21.0GB  extended                    
 5      64.5kB  10.2GB  10.2GB  logical   ext3              
 6      10.2GB  20.5GB  10.2GB  logical   ext3              
 7      20.5GB  21.0GB  526MB   logical   ext3              
 2      21.0GB  64.9GB  43.8GB  primary                     
 3      64.9GB  250GB   185GB   primary                     


Warning: Unable to open /dev/sr0 read-write (Read-only file system).  /dev/sr0
has been opened read-only.
Error: /dev/sr0: unrecognised disk label                                  

Warning: Unable to open /dev/fd0 read-write (Read-only file system).  /dev/fd0
has been opened read-only.
Error: /dev/fd0: unrecognised disk label                                  


```

The ones that don't show a file system are encrypted.

jdb

---

### Post by jdb on 2009-09-29
> **AlexInBlack said:**
> 
I've been using Xubuntu 9.04 (amd64) installed via LiveUSB. I'm pretty sure it's not a problem with the LiveUSB OS (although it never starts up with X, as in I have to type "startx" every time I boot it up)

You might try installing with a liveCD instead of the LiveUSB.
When I booted to a LiveCD on my last post it came right up in Xubuntu.
I've never had to type startx with a liveCD.
I've installed Xubuntu on a lot of computers using a liveCD & have never had any problems.

jdb

---

### Post by AlexInBlack on 2009-09-29
Output via "sudo parted -l"
```

Model: ATA WDC WD2500BEVT-2 (scsi)
Disk /dev/sda: 250GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type      File system  Flags
 2      32.3kB  535MB   535MB   primary   ext3              
 1      535MB   52.5GB  51.9GB  primary   ntfs         boot 
 3      52.5GB  244GB   192GB   extended                    
 5      52.5GB  225GB   173GB   logical   ext3              
 6      225GB   236GB   10.5GB  logical                     
 7      236GB   244GB   8390MB  logical   linux-swap        


Model: BUFFALO USB Flash Disk (scsi)
Disk /dev/sdb: 2064MB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
 1      32.3kB  2056MB  2056MB  primary  fat16        boot 

```

When 9.10 comes around, I'll try a reinstall of Xubuntu via a LiveCD if nothing else works.

---

### Post by jdb on 2009-09-30
> **AlexInBlack said:**
> Output via "sudo parted -l"
```

Model: ATA WDC WD2500BEVT-2 (scsi)
Disk /dev/sda: 250GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type      File system  Flags
 2      32.3kB  535MB   535MB   primary   ext3              
 1      535MB   52.5GB  51.9GB  primary   ntfs         boot 
 3      52.5GB  244GB   192GB   extended                    
 5      52.5GB  225GB   173GB   logical   ext3              
 6      225GB   236GB   10.5GB  logical                     
 7      236GB   244GB   8390MB  logical   linux-swap        


Model: BUFFALO USB Flash Disk (scsi)
Disk /dev/sdb: 2064MB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
 1      32.3kB  2056MB  2056MB  primary  fat16        boot 

```

When 9.10 comes around, I'll try a reinstall of Xubuntu via a LiveCD if nothing else works.

There's some magic at the begining of a partition that identifies it's type.
Since sda6 doesn't show a type it got mangled somehow.
My encrypted partitions don't show a type because they look like random noise.
I'll keep my fingers crossed for you on the live CD install.

jdb

---

### Post by AlexInBlack on 2009-11-07
I installed Xubuntu 9.10 via LiveUSB. I didn't like the password I entered, so right after booting and enabling a wireless network, I changed it by booting into recovery mode and using:
```
passwd username
```

When I rebooted, I got locked into a cycle of login screens. My partitions were all the same (I just installed over them, making sure to format them as ext3). The only thing different from my 9.04 install was that I enabled the option: "Require password to log in and to decrypt home folder"

I then reinstalled, but this time, without requiring the password to decrypt home folder. It seems to work fine now.

I still get messages on the boot-up screen before the GRUB menu. I don't know what they are, but they do kind of worry me and look messy, so I attached a picture. The last two lines are what I have no idea are about.
The picture's a bit blurry. The last two lines are:
PXE-E61: Media test failure, check cable
PXE-M0F: Exiting PXE ROM

I realize that Xubuntu isn't supported and Ubuntu 9.10 in general still isn't, but I appreciate any input.

---

### Post by jdb on 2009-11-07
> **AlexInBlack said:**
> PXE-E61: Media test failure, check cable
PXE-M0F: Exiting PXE ROM



PXE ROM is built into the network card & is used to boot to a network,
mostly for computers that don't have a disk drive.

The message does no harm & judging from google it is fairly common.

jdb

---

### Post by thomasaaron on 2009-11-09
When you see the System76 splash screen, press F2 to enter the BIOS setup utility. From there, tab over the "Boot Options."

In Boot Options, set your hard drive as the first boot device. Does that fix the problem?

---

### Post by AlexInBlack on 2009-11-24
Setting the HD as the first boot device got rid of that screen. Thanks.
So far, Xubuntu 9.10 by LiveUSB without an encrypted /home on my daru3 seems to work fine.

---

