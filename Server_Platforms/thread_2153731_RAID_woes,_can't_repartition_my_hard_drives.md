---
title: "RAID woes, can't repartition my hard drives"
date: 2013-06-12
forum: Server Platforms
---

### Post by ladasky on 2013-06-12
Hi folks,

_[A little bird told me]("http://ubuntuforums.org/showthread.php?t=2153670&p=12687694#post12687694")_ that the Server forums would be the best place to seek advice on RAID.  I've just tried to delete the partitions on a system that had (and maybe still has vestiges of) a RAID1, built with **mdadm** and the old MS-DOS MBR.  I thought I had a perfect configuration to install Ubuntu 13.04 along-side 12.04, but _[my installation attempts have aborted]("http://ubuntuforums.org/showthread.php?t=2153652")_ at the *grub-install* step.

It was suggested that I upgrade from MBR to gpt, or LVM.  I don't actually need more than four physical partitions on each hard drive, an amount which MBR can handle.  But something was standing in the way of my installation process.  From some of the prompts I was getting when trying to install 13.04, I felt like I was getting hints to use logical, rather than physical, volume management.

I backed up my */home* directory to an external drive, booted from the 13.04 live disk, installed *mdadm*, attempted to disassemble the RAID, and then reformat the hard drives.  I'm stuck.  I can't seem to create a new partition table.  GParted complains thus: "Partition(s) 2 on /dev/sda have been written, but we have been unable to inform the kernel of the change, probably because it/they are in use.  As a result, the old partition(s) will remain in use.  You should reboot now before making further changes."  I have gotten similar messages when I try to create partitions: the system claims that I'm using partitions that I have only just created.

I found some rather _[dated instructions for killing an old RAID setup]("http://ubuntuforums.org/showthread.php?t=884556")_, once and for all.  I followed these steps, but they aren't working for me.

Thanks for any help you can provide!

---

### Post by darkod on 2013-06-12
1. Make sure you are not mounting any partitions!
2. Make sure you unmount any swap partition that might exist on the disk if you are doing this from live mode, because swap gets mounted in live mode automatically to speed it up!

There is no special procedure for deleting mdadm setup/partitions, especially if you plan to write new partition table on the disk anyway. If you want to use existing partition that was part of mdadm array, you need to zero the superblock first, so that it will be considered as a brand new partition never used in mdadm.
But creating new partition table removes all partitions with their superblocks anyway, so this step is not needed.

From live mode can you post the output of:
```
cat /proc/mdstat
sudo parted -l
df -h
```

---

### Post by ladasky on 2013-06-12
Thank you darkod, here is the output you requested -- plus, the output of the *mount* command:

```
ubuntu@ubuntu:~$ cat /proc/mdstat

Personalities : [raid1] 
md127 : inactive sda2[0](S)
      20955136 blocks super 1.2
       
unused devices: <none>



ubuntu@ubuntu:~$ sudo parted -l

Model: ATA WDC WD6401AALS-0 (scsi)
Disk /dev/sda: 640GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt

Number  Start  End  Size  File system  Name  Flags


Model: ATA WDC WD7501AALS-0 (scsi)
Disk /dev/sdb: 750GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt

Number  Start  End  Size  File system  Name  Flags


Warning: Unable to open /dev/sr0 read-write (Read-only file system).  /dev/sr0
has been opened read-only.
Error: Can't have a partition outside the disk!                           



ubuntu@ubuntu:~$ df -h

Filesystem      Size  Used Avail Use% Mounted on
/cow            3.9G  499M  3.5G  13% /
udev            3.9G   12K  3.9G   1% /dev
tmpfs           799M  900K  798M   1% /run
/dev/sr0        785M  785M     0 100% /cdrom
/dev/loop0      738M  738M     0 100% /rofs
none            4.0K     0  4.0K   0% /sys/fs/cgroup
tmpfs           3.9G  1.2M  3.9G   1% /tmp
none            5.0M     0  5.0M   0% /run/lock
none            3.9G  148K  3.9G   1% /run/shm
none            100M   48K  100M   1% /run/user



ubuntu@ubuntu:~$ mount

/cow on / type overlayfs (rw)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
udev on /dev type devtmpfs (rw,mode=0755)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
/dev/sr0 on /cdrom type iso9660 (ro,noatime)
/dev/loop0 on /rofs type squashfs (ro,noatime)
none on /sys/fs/cgroup type tmpfs (rw)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880)
none on /run/shm type tmpfs (rw,nosuid,nodev)
none on /run/user type tmpfs (rw,noexec,nosuid,nodev,size=104857600,mode=0755)
gvfsd-fuse on /run/user/ubuntu/gvfs type fuse.gvfsd-fuse (rw,nosuid,nodev,user=ubuntu)
```

I am leaving this system turned on until I resolve the problem.  I don't want things to get changed by a reboot.

---

### Post by darkod on 2013-06-12
Have you tried something like:
```
sudo mdadm --stop /dev/md127
sudo mdadm --zero-superblock /dev/sda2
```

Then open /etc/mdadm/mdadm.conf and remove all ARRAY definitions that might be there. Save and close the file.

That should be it. You can try making partitions on the disks with or without rebooting.

---

### Post by ladasky on 2013-06-12
Thanks again, darkod, for your continued help.

> **darkod said:**
> Have you tried something like:
```
sudo mdadm --stop /dev/md127
sudo mdadm --zero-superblock /dev/sda2
```

I have done things like this before, but I just did it again.  I keep getting stray logical partitions made, which I then have to remove, when GParted does the job half-way.

> **darkod said:**
> Then open /etc/mdadm/mdadm.conf and remove all ARRAY definitions that might be there. Save and close the file.

My *mdadm.conf* had no array definitions, so I didn't edit it.

```
# mdadm.conf
#
# Please refer to mdadm.conf(5) for information about this file.
#

# by default (built-in), scan all partitions (/proc/partitions) and all
# containers for MD superblocks. alternatively, specify devices to scan, using
# wildcards if desired.
#DEVICE partitions containers

# auto-create devices with Debian standard permissions
CREATE owner=root group=disk mode=0660 auto=yes

# automatically tag new arrays as belonging to the local system
HOMEHOST <system>

# instruct the monitoring daemon where to send mail alerts
MAILADDR root

# definitions of existing MD arrays

# This file was auto-generated on Wed, 12 Jun 2013 07:51:31 +0000
# by mkconf $Id$
```

> **darkod said:**
> That should be it. You can try making partitions on the disks with or without rebooting.

Ah well, I made some progress, but I'm still not all the way there.  I got all the way through */dev/sda* this time, but then I got a *mkfs* error on */dev/sdb*.   The computer claims that */dev/sdb1* is in use.  I have seen this kind of error several times.   Here is the error output from *gparted_details.htm*:

```
GParted 0.12.1 --enable-libparted-dmraid

Libparted 2.3
Create Primary Partition #1 (ext4, 30.00 GiB) on /dev/sda  00:00:02    ( SUCCESS )
     	
create empty partition  00:00:00    ( SUCCESS )
     	
path: /dev/sda1
start: 2,048
end: 62,916,607
size: 62,914,560 (30.00 GiB)
set partition type on /dev/sda1  00:00:00    ( SUCCESS )
     	
new partition type: ext4
create new ext4 file system  00:00:02    ( SUCCESS )
     	
mkfs.ext4 -j -O extent -L "OS1a" /dev/sda1
     	
Filesystem label=OS1a
OS type: Linux
Block size=4096 (log=2)
Fragment size=4096 (log=2)
Stride=0 blocks, Stripe width=0 blocks
1966080 inodes, 7864320 blocks
393216 blocks (5.00%) reserved for the super user
First data block=0
Maximum filesystem blocks=4294967296
240 block groups
32768 blocks per group, 32768 fragments per group
8192 inodes per group
Superblock backups stored on blocks:
32768, 98304, 163840, 229376, 294912, 819200, 884736, 1605632, 2654208,
4096000

Allocating group tables: done
Writing inode tables: done
Creating journal (32768 blocks): done
Writing superblocks and filesystem accounting information: done

mke2fs 1.42.5 (29-Jul-2012)

========================================
Create Primary Partition #2 (ext4, 30.00 GiB) on /dev/sda  00:00:02    ( SUCCESS )
     	
create empty partition  00:00:00    ( SUCCESS )
     	
path: /dev/sda2
start: 62,916,608
end: 125,831,167
size: 62,914,560 (30.00 GiB)
set partition type on /dev/sda2  00:00:00    ( SUCCESS )
     	
new partition type: ext4
create new ext4 file system  00:00:02    ( SUCCESS )
     	
mkfs.ext4 -j -O extent -L "OS2a" /dev/sda2
     	
Filesystem label=OS2a
OS type: Linux
Block size=4096 (log=2)
Fragment size=4096 (log=2)
Stride=0 blocks, Stripe width=0 blocks
1966080 inodes, 7864320 blocks
393216 blocks (5.00%) reserved for the super user
First data block=0
Maximum filesystem blocks=4294967296
240 block groups
32768 blocks per group, 32768 fragments per group
8192 inodes per group
Superblock backups stored on blocks:
32768, 98304, 163840, 229376, 294912, 819200, 884736, 1605632, 2654208,
4096000

Allocating group tables: done
Writing inode tables: done
Creating journal (32768 blocks): done
Writing superblocks and filesystem accounting information: done

mke2fs 1.42.5 (29-Jul-2012)

========================================
Create Primary Partition #3 (ext4, 536.17 GiB) on /dev/sda  00:00:05    ( SUCCESS )
     	
create empty partition  00:00:00    ( SUCCESS )
     	
path: /dev/sda3
start: 125,831,168
end: 1,250,263,039
size: 1,124,431,872 (536.17 GiB)
set partition type on /dev/sda3  00:00:01    ( SUCCESS )
     	
new partition type: ext4
create new ext4 file system  00:00:04    ( SUCCESS )
     	
mkfs.ext4 -j -O extent -L "HomeA" /dev/sda3
     	
Filesystem label=HomeA
OS type: Linux
Block size=4096 (log=2)
Fragment size=4096 (log=2)
Stride=0 blocks, Stripe width=0 blocks
35143680 inodes, 140553984 blocks
7027699 blocks (5.00%) reserved for the super user
First data block=0
Maximum filesystem blocks=4294967296
4290 block groups
32768 blocks per group, 32768 fragments per group
8192 inodes per group
Superblock backups stored on blocks:
32768, 98304, 163840, 229376, 294912, 819200, 884736, 1605632, 2654208,
4096000, 7962624, 11239424, 20480000, 23887872, 71663616, 78675968,
102400000

Allocating group tables: done
Writing inode tables: done
Creating journal (32768 blocks): done
Writing superblocks and filesystem accounting information: done

mke2fs 1.42.5 (29-Jul-2012)

========================================
Create Primary Partition #4 (ext4, 30.00 GiB) on /dev/sdb  00:00:02    ( ERROR )
     	
create empty partition  00:00:01    ( SUCCESS )
     	
path: /dev/sdb1
start: 2,048
end: 62,916,607
size: 62,914,560 (30.00 GiB)
set partition type on /dev/sdb1  00:00:01    ( SUCCESS )
     	
new partition type: ext4
create new ext4 file system  00:00:00    ( ERROR )
     	
mkfs.ext4 -j -O extent -L "OS1b" /dev/sdb1
     	
mke2fs 1.42.5 (29-Jul-2012)
/dev/sdb1 is apparently in use by the system; will not make a filesystem here!

========================================
Create Primary Partition #5 (ext4, 30.00 GiB) on /dev/sdb

========================================
Create Primary Partition #6 (ext4, 536.17 GiB) on /dev/sdb

========================================
Create Primary Partition #7 (linux-swap, 16.00 GiB) on /dev/sdb

========================================

```

As you can see, my */dev/sdb* is a bit larger than my */dev/sda*.  The drives used to be identical, but one of my 640 GB drives was returned (under warranty). Western Digital sent me a 750 GB drive.  Apparently they're out of the 640's.

My plan is to have three RAID1 partitions -- one for Ubuntu 13.04 root, one for a future Ubuntu release, and one for */home*.  Swap goes in the extra space on */dev/sdb*, and is not part of the RAID.


**EDIT: follow-up: The pull-down menu in GParted now shows that I have a */dev/md127*, 8.00 GiB in size**, in addition to the* /dev/sda* and */dev/sdb* that I expect.  It also appears in */proc/mdstat*:

```
ubuntu@ubuntu:~$ cat /proc/mdstat

Personalities : [raid1] 
md127 : active raid1 sdb1[1]
      8384448 blocks super 1.2 [2/1] [_U]
      
unused devices: <none>
```


HOW did this */dev/md127* get created, and why is it being given RAID status when I haven't even started with the RAID part of my partitioning?  Why is it 8.00 GiB?  This matches the size of my old swap partition (which was on the RAID), but it does not match the size of any of the new partitions I am trying to create.

---

### Post by darkod on 2013-06-12
Did you try writing a new partition table on both? Try from the terminal, not with Gparted (shouldn't make a difference, but give it a shot):
```
sudo parted /dev/sda
mklabel msdos (or gpt if you prefer gpt table)
select /dev/sdb
mklabel msdos
quit
```

After that reboot and try again creating partitions with Gparted.

Note that if you use gpt table you have to make a small 1MiB partition with NO filesystem and with the bios_grub flag set on it. This is needed for grub2 to install correctly on gpt disks.

Also, did you check if you have some fakeraid meta data on the disks? Just in case, try:
```
sudo dmraid -Er /dev/sda
sudo dmraid -Er /dev/sdb
```

Remove any meta data found.

---

### Post by ladasky on 2013-06-12
> **darkod said:**
> Did you check if you have some fakeraid meta data on the disks? Just in case, try:
```
sudo dmraid -Er /dev/sda
sudo dmraid -Er /dev/sdb
```

Remove any meta data found.

When I first started using RAID about three years ago, I read about dmraid/fakeraid and chose not to use it.  Still, I checked, and the system was clear of any fakeraid data.

```
ubuntu@ubuntu:~$ sudo dmraid -Er /dev/sda
no raid disks and with names: "/dev/sda"
ubuntu@ubuntu:~$ sudo dmraid -Er /dev/sdb
no raid disks and with names: "/dev/sdb"
ubuntu@ubuntu:~$ sudo parted /dev/sda
```

> **darkod said:**
> Did you try writing a new partition table on both? Try from the terminal, not with Gparted (shouldn't make a difference, but give it a shot):
```
sudo parted /dev/sda
mklabel msdos (or gpt if you prefer gpt table)
select /dev/sdb
mklabel msdos
quit
```

After that reboot and try again creating partitions with Gparted.

Note that if you use gpt table you have to make a small 1MiB partition with NO filesystem and with the bios_grub flag set on it. This is needed for grub2 to install correctly on gpt disks.

OK, so after I stopped and zeroed the mysterious */dev/md127* once again, I was able to execute the *parted* commands that you recommended.  Also, THANK YOU for the hint that gpt needs an unformatted partition for Grub2, I included one on each drive.  (I needed more than four partitions after all!)  For some reason, I was unable to set the *bios-grub* flags in my newly-created partitions until after a reboot, but that was OK.

On reboot, I have the following:

```
ubuntu@ubuntu:~$ sudo parted -l

Model: ATA WDC WD6401AALS-0 (scsi)
Disk /dev/sda: 640GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt

Number  Start   End     Size    File system  Name  Flags
 1      1049kB  2097kB  1049kB                     bios_grub
 2      2097kB  32.2GB  32.2GB  ext4
 3      32.2GB  64.4GB  32.2GB  ext4
 4      64.4GB  640GB   576GB   ext4


Model: ATA WDC WD7501AALS-0 (scsi)
Disk /dev/sdb: 750GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt

Number  Start   End     Size    File system     Name  Flags
 1      1049kB  2097kB  1049kB                        bios_grub
 2      2097kB  32.2GB  32.2GB  ext4
 3      32.2GB  64.4GB  32.2GB  ext4
 4      64.4GB  640GB   576GB   ext4
 5      640GB   657GB   17.2GB  linux-swap(v1)


Warning: Unable to open /dev/sr0 read-write (Read-only file system).  /dev/sr0
has been opened read-only.
Error: Can't have a partition outside the disk!
```

I think that I'm finally ready for *mdadm*.  When I accomplish that, I will mark this task as Solved.

---

### Post by ladasky on 2013-06-12
My efforts with *mdadm* succeeded, and I am ready to mark this thread as Solved.  (Hey, where exactly did the **"mark as solved"** button go?) Thanks as always, darkod.

Unfortunately: the whole reason that I was going through this exercise was to try to install 13.04 on a RAID1, and it STILL DOES NOT WORK. :mad:  _[Just as before]("http://ubuntuforums.org/showthread.php?t=2140218")_, I am getting a "fatal error" at the *grub-install* stage. I've just spent six weeks going in a giant circle.  Actually, I've taken a step backwards -- now that I've killed my original array, and no longer have a working 12.04 system on my hard drive!  ](*,)

Darkod, you were also the person who helped me the most in that previous thread.  I'm going to try one more idea... and then revive the thread if I have more questions.  See you there? :(

---

### Post by Iowan on 2013-06-12
I marked it [SOLVED] for you. Hopefully, one of these will be helpful:
[http://ubuntuforums.org/showthread.php?t=2151638](http://ubuntuforums.org/showthread.php?t=2151638)
[http://ubuntuforums.org/showthread.php?t=2121377](http://ubuntuforums.org/showthread.php?t=2121377)

---

### Post by ladasky on 2013-06-12
Thanks, Iowan.  I'll subscribe to those threads and, hopefully, I'll remember to look through my subscribed threads the next time I have one to mark.

---

### Post by darkod on 2013-06-13
It shouldn't be a problem, but just for future reference, you shouldn't have formatted the partitions as ext4. That's why I prefer making partitions for raid with parted, and not Gparted. Because parted always creates partitions without any filesystem. You format them yourself later.

For mdadm, you don't format the partitions as ext4. You leave them without any filesystem. After you create the md devices, you format the md devices as ext4 and use them. Not the physical partitions.

---

### Post by ladasky on 2013-06-14
> **darkod said:**
> It shouldn't be a problem, but just for future reference, you shouldn't have formatted the partitions as ext4. That's why I prefer making partitions for raid with parted, and not Gparted. Because parted always creates partitions without any filesystem. You format them yourself later.

GParted, at least the version that came with the 13.04 installation, has what looked like a new feature to me: the option to create a partition, but not format it.  That's what you told me to do for the little boot partitions and, as you can see, it worked.  

> **darkod said:**
> For mdadm, you don't format the partitions as ext4. You leave them without any filesystem. After you create the md devices, you format the md devices as ext4 and use them. Not the physical partitions.

[Smacks forehead] Of course!  That's also what I did when I built my RAID1 using the text-based interface on the old "alternate install" disks.  When you don't do an arcane task for a full year -- you can forget the details.

Now -- did this premature formatting block somehow my *grub-install*, or didn't it?  It would be strange if it did.  As you can see, both */dev/sda1* and */dev/sdb1*, the partitions intended for Grub, were unformatted.

If you look at _[the other thread]("http://ubuntuforums.org/showthread.php?t=2140218&page=2&p=12688979#post12688979")_, you'll see that I've decided to go with LVM, given that the Ubuntu installer promotes it.  I will now investigate LVM mirroring.

EDIT: Darn it, I started that investigation, and wouldn't you know it -- _[here's you, Darkod]("http://ubuntuforums.org/showthread.php?t=2134520&p=12598583#post12598583")_, recommending installing LVM on top of an *mdadm*-administered RAID!

---

### Post by darkod on 2013-06-14
:)

It shouldn't affect the grub2 install since the small partitions are correct. Maybe a glitch or a bug. You can also try adding grub2 later. If the whole system installed fine, just adding grub2 is easy.

---

