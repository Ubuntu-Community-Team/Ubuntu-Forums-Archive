---
title: "are there options for RAID?"
date: 2011-11-10
forum: Server Platforms
---

### Post by bjchmod on 2011-11-10
I'm building a new server and I cannot get RAID configured through mdadm.  Are there other options for software RAID?  Is my only option to buy a hardware RAID card?

This is a new installation of Ubuntu 11.10 server.  I have 3 identical hard drives, so I put in one hard drive and installed the OS to it.  Then I added the other 2 hard drives and tried to build the RAID array onto them (RAID 1).  I did the fdisk on each drive, which are sda and sdb (OS is on sdc).  Then I try to zero the superblock and I get "couldn't open /dev/sda for write - not zeroing".  I google this and it seems to be a very common problem with mdadm.  I can't figure out how to get around it.  These drives have never been used in a Linux system before but they previously were used in a Windows system.  I erased all existing partitions with fdisk and added a new primary partition to each drive, of type "fd".

---

### Post by Jonathan L on 2011-11-11
> **bjchmod said:**
> I'm building a new server and I cannot get RAID  configured through mdadm.  Are there other options for software RAID?   Is my only option to buy a hardware RAID card?

This is a new installation of Ubuntu 11.10 server.  I have 3 identical  hard drives, so I put in one hard drive and installed the OS to it.   Then I added the other 2 hard drives and tried to build the RAID array  onto them (RAID 1).  I did the fdisk on each drive, which are sda and  sdb (OS is on sdc).  Then I try to zero the superblock and I get  "couldn't open /dev/sda for write - not zeroing".  I google this and it  seems to be a very common problem with mdadm.  I can't figure out how to  get around it.  These drives have never been used in a Linux system  before but they previously were used in a Windows system.  I erased all  existing partitions with fdisk and added a new primary partition to each  drive, of type "fd".

Hi BJ

In summary: no, you don't have to buy a hardware card.

I'll  confess I've only done it with the installer (and for 10.04 server),  but I'm sure the process is similar.  The following are from my notes  for configuring two disks as RAID1 which is the system disk

[LIST]
[*]Partition Disks -- Manual
[*]sda and sda both show as free space (delete things if not)
[*]Partition sda (in my case ext4 + swap)
[*]Partition sdb (identically to first disk)
[*]Disks show
[/LIST]
```
sda #1 primary XXX GB ext4
sda #5 logical YYY GB swap
sdb #1 primary XXX GB ext4
sdb #5 logical YYY GB swap
```
[LIST]
[*]Configure software RAID
[*]Confirm / Formats
[*]Create MD device
[*]Choose RAID1 (choices 0, 1, 5, 6, 10)
[*]Choose number of disks for array, default 2
[*]Choose number of spare disks, default 0
[*]Select members of RAID set: sda1 and sdb1
[*]Confirm
[*]Repeat above from "Create MD" for each RAID device
[*]Finish making MD devices
[*]Now list shows
[/LIST]
```
RAID1 device #0 - XXX GB Unknown
     #1           XXX GB       ext4
RAID1 device #1 - YYY GB Software RAID device
     #1           YYY GB
                  ZZZ kB       unusable
SCSI1 (0,0,0) (sda) ...
     #1  primary  XXX GB    K raid
     #5  logical  YYY GB    K raid
SCSI1 (0,0,0) (sdb) ...
     #1  primary  XXX GB    K raid
     #5  logical  YYY GB    K raid
```
[LIST]
[*]Select RAID1 device #0, #1 (ie line with ext4)
[*]Use as "Ext4 journaling file system", format, mount point
[*]Done setting up the partition
[*]Repeat for subsequent RAID sets (as swap, in my case)
[*]Finish partitioning and write changes to disk
[*]Want to boot if RAID becomes degraded: yes (or no if you prefer)
[*]Write changes to disk: yes
[*]Watch it format
[/LIST]

Perhaps  that's some help: if you have a fresh install you might be able to use  the installer.  I'll see if I can find out how you either restart the  installer tool or the appropriate mdadm/fdisk commands.

Kind regards,
Jonathan.

---

### Post by rubylaser on 2011-11-11
Since, you've added partitions to sda and sdb, you'd want to use sda1 and sdb1 for your mdadm devices.  Also, since you haven't setup mdadm on them before, there's no reason to zero the superblock.  If you want to do this from the command line, here are your steps...

```
sudo -i
```

If you've tried to setup mdadm in the past, it's likely that you have any array setup and have superblock info on your disks, if so, follow these steps first.

```
mdadm -E /dev/sda1
```
or 
```
mdadm -E /dev/sda
```
and if any array information shows up, you'll need to zero the superblocks, stop any running arrays, and remove your /etc/mdadm/mdadm.conf file like the following, otherwise, skip down to the New Array Setup section and proceed from there.
```
mdadm --zero-superblock /dev/sda
```
```
mdadm --zero-superblock /dev/sdb
```
```
mdadm --zero-superblock /dev/sda1
```
```
mdadm --zero-superblock /dev/sdb1
```
Look at the output of this...
```
cat /proc/mdstat
```
stop any running arrays...
```
mdadm --stop /dev/md0
```
Then remove your current /etc/mdadm/mdadm.conf file.
```
echo -n > /etc/mdadm/mdadm.conf
```

**New Array Setup**
```
mdadm --create --verbose /dev/md0 --level=1 --raid-devices=2 /dev/sd[ab]1
```
You can check the status of the sync like this...
```
watch cat /proc/mdstat
```

Now that we have set up the array, we need to edit the mdadm configuration so it knows how to reassemble it when the system boots.
```
echo "DEVICE partitions" > /etc/mdadm/mdadm.conf
echo "HOMEHOST fileserver" >> /etc/mdadm/mdadm.conf
echo "MAILADDR root@localhost" >> /etc/mdadm/mdadm.conf
mdadm --detail --scan >> /etc/mdadm/mdadm.conf
```

Now that the array is built we need to format it. What filesystem you choose is up to you, but I would recommend ext4. Note: In this example, I used ext4.
```
mkfs.ext4 /dev/md0
```

Next, add your array to fstab so it will be mounted at boot.
```
nano /etc/fstab
```
 
Then, paste this in...
```
/dev/md0	/storage	    ext4	defaults	0	0
```

Create the mount point...
```
mkdir /storage
```

And mount it...
```
mount -a
```

Your array should now be mounted on /storage and should survive a reboot.  Hope that helps.

---

### Post by bjchmod on 2011-11-11
I have tried to set up an array already but apparently nothing was saved.

This command "mdadm -E /dev/sda1" says "cannot open   no such file or directory".

If I try "mdadm --zero-superblock /dev/sda" I get the message in my first post-
"couldn't open /dev/sda for write - not zeroing".

I went through the steps to start a new mdadm.conf, then when I run "mdadm --create --verbose /dev/md0 --level=1 --raid-devices=2 /dev/sd[ab]1" I get the following output:

[IMG]http://i15.photobucket.com/albums/a370/bjd70/Linuxmessages/photo268b.jpg[/IMG]

but if I go into fdisk to check partitions it seems that the partition is created properly:

[IMG]http://i15.photobucket.com/albums/a370/bjd70/Linuxmessages/photo269b.jpg[/IMG]

---

### Post by rubylaser on 2011-11-11
Can you provide the output from these two commands...
```
fdisk -l
```
```
mount
```
```
lsof
```

They'll both need to be done as root. Also, have you made sure your disks aren't part of a [FakeRAID]("http://www.righteoushack.net/?p=197")?

---

### Post by bjchmod on 2011-11-11
> **rubylaser said:**
> Can you provide the output from these two commands...
```
fdisk -l
``````
mount
``````
lsof
```They'll both need to be done as root. Also, have you made sure your disks aren't part of a [FakeRAID]("http://www.righteoushack.net/?p=197")?


fdisk:

[IMG]http://i15.photobucket.com/albums/a370/bjd70/Linuxmessages/IMG_2498b.jpg[/IMG]

mount:

[IMG]http://i15.photobucket.com/albums/a370/bjd70/Linuxmessages/IMG_2499b.jpg[/IMG]

lsof- produces several screens of listing.  I can't capture it all.


I don't have any form of raid running right now.  I have 3 hard drives plugged into the primary and secondary IDE controllers on the motherboard.  I removed the CD drive when I connected the 2 drives that I want to RAID.

I'm not sure what that last entry is in the fdisk output, I only have 3 physical hard drives connected, and they are identical.  Also I don't understand why it is using different heads and cylinders on the different drives, but I recall that on larger drives different translation schemes are used and that is OK as long as they arrive at the correct drive size.

---

