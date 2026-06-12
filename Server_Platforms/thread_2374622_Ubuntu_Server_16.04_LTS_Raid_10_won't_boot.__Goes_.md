---
title: "Ubuntu Server 16.04 LTS Raid 10 won't boot.  Goes to initramfs prompt: what now?"
date: 2017-10-17
forum: Server Platforms
---

### Post by jphat on 2017-10-17
Hi All

A thousand apologies for the long email, I'm a bit out of my depth and have bit off more than I can chew.  I'm relatively new to Ubuntu though have experimented with it on desktops and old laptops in the past.  I took an old windows server fore my home and created a Raid 10 (with 4 hard drives) setup running Ubuntu Server and then loaded a GUI (the essentials only I think if I remember correctly - I'm not ready to run without a GUI :D).  All was well although it had some issue where I needed to run an older kernel or it wouldn't boot after I had loaded the GUI.

Long story short - I loaded a pile of data from various sources onto the server and then left the server alone (and off) for a month or two whilst I was away on work.  I came back and it booted up fine.  Because of where I was in the house though I couldn't plug it in with an ethernet cable into the router so I took a TP-Link rtl8192cu usb stick and plugged it in for Wifi access.  The usb stick could be seen but would not work so I tried to install a working driver as per the information on ([https://github.com/pvaret/rtl8192cu-fixes):](https://github.com/pvaret/rtl8192cu-fixes):)
"Installation

Ensure you have the necessary prerequisites installed:
sudo apt-get update
sudo apt-get install git linux-headers-generic build-essential dkms
Clone this repository:
git clone [https://github.com/pvaret/rtl8192cu-fixes.git](https://github.com/pvaret/rtl8192cu-fixes.git)
Set it up as a DKMS module:
sudo dkms add ./rtl8192cu-fixes
Build and install it:
sudo dkms install 8192cu/1.10
Refresh the module list:
sudo depmod -a
Ensure the native (and broken) kernel driver is blacklisted:
sudo cp ./rtl8192cu-fixes/blacklist-native-rtl8192.conf /etc/modprobe.d/
And reboot. You're done."

Followed all that blindly and now I'm in the dwang.

I can no longer boot and I cannot see other different kernel's to load as I could before (they are now the same except under *Advanced options for Ubuntu saying -generic, -generic (upstart) or -generic (recovery mode) at the end of the kernel name - Ubuntu, with Linux 4.4.0-87-).  They all do not boot and result in the same output.

After going through a long load of various things it gets stuck at:

Begin: Running /scripts/local-block ... mdadm: Devices UUID-975718c3:..... and UUID-975718c3:.... have the same name: /dev/md/0
mdadm: Duplicate MD device names in conf file were found.
done.
done.
Gave up waiting for root device. Common problems:
and then..
ALERT! UUID=4d834432-.... does not exist.  Dropping to a shell!

BusyBox v1.22.1 (Ubuntu 1:1.22.0-15ubuntu1) built-in shell (ash)
Enter 'help' for a list of built-in commands.

(initramfs)

I do not know what to do from this prompt?  As I recall I partioned etc from the initial setup, I didn't knowingly use mdadm.  After a bit of googling I tried "cat /proc/mdstat" which returned:
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10]
unused devices: <none>

It says nothing about md devices?
I also tried "cat /etc/mdadm/mdadm.conf" which returns a long mostly hashed (#) out section but also two sections of arrays at the bottom:
```
# definitions of existing MD arrays
ARRAY /dev/md/0 metadata=1.2 UUID=975718c3:.... name=ubuntu:0
ARRAY /dev/md/2 metadata=1.2 UUID=8a79d5e6:...  name=ubuntu:2
ARRAY /dev/md/1 metadata=1.2 UUID=7285adee:...  name=ubuntu:1
```

```
#This file was auto-generated on Fri, 28 Jul 2017 12:46:03 +0200
#by mkconf $Id$
ARRAY /dev/md/ddf0 metadata=ddf UUID=9bf60781:...
ARRAY /dev/md/2 metadata=1.2 name=ubuntu:2 UUID=8a79d5e6:...
ARRAY /dev/md/1 metadata=1.2 name=ubuntu:1 UUID=7285adee....
ARRAY /dev/md/0 metadata=1.2 name=ubuntu:0 UUID=975718c3:...
ARRAY /dev/md126 container=/dev/md/ddf0 member=0 UUID=3e1e8668:....
```

I can see there's duplicate names in the two ARRAY entries in the above files but don't know how to change that  or even if that is a problem, any help would be appreciated as I'm unsure how to get anything done from the (initramfs) prompt and suspect the raid array is not being loaded/compiled or seen.

Thanks in advance,

Josh

---

### Post by howefield on 2017-10-19
Thread moved to the "*Server Platforms*" forum, potentially a better fit.

---

### Post by darkod on 2017-10-19
When you say you "did not knowingly use mdadm" does that mean you also didn't use setting up software RAID during installation? Because you say you have raid10 but didn't use mdadm. That makes a confusion whether you used other type of raid (bios, hw) or you simply used Software RAID option during install which is in fact mdadm but without you knowing it...

Because the mdadm.conf does have ARRAY definitions which makes it rare to happen if you didn't use mdadm.

---

### Post by jphat on 2017-10-19
Hi, I setup the partitions from the Ubuntu launch screen on installation, so I don't think I used mdadm (unless the setup uses it in the "background").

---

### Post by darkod on 2017-10-19
No, it doesn't. When setting up partitions you have to go into the option "Configure Software RAID" and configure the raid part there. If you don't, no mdadm raid is set up. Unless you didn't start with fresh clean disks and they already had mdadm raid on them. In that case it can recognize it and list them in the partitions section, so you could be easily configuring the raid devices instead of the physical partitions without knowing it.

Download the Ubuntu Desktop 16.04 (if you don't have it already) and create a boot usb or dvd with it. Then boot the computer from it into live mode (Try Ubuntu). Open terminal and paste the output of the following commands:
```
sudo blkid
lsblk
sudo parted -l
```

That will help figure out which partitions you have there.

---

### Post by jphat on 2017-10-19
Hi Darko

```

ubuntu@ubuntu:~$ sudo blkid
/dev/sdd1: UUID="975718c3-c315-01ea-3582-1c8a29349f1f" UUID_SUB="51af3e50-15bf-eb87-e409-5ba03174e687" LABEL="ubuntu:0" TYPE="linux_raid_member" PARTUUID="02ac51d3-01"
/dev/sdd6: UUID="7285adee-cbc5-3247-ec01-52febebfb590" UUID_SUB="23ec15c2-00da-612b-7dc3-7611ae3049e9" LABEL="ubuntu:1" TYPE="linux_raid_member" PARTUUID="02ac51d3-06"
/dev/sde1: LABEL="UBUNTU 17_0" UUID="62F3-8F04" TYPE="vfat" PARTUUID="15ca4a7b-01"
/dev/loop0: TYPE="squashfs"
/dev/sda1: UUID="975718c3-c315-01ea-3582-1c8a29349f1f" UUID_SUB="356cd815-0c6e-3ebf-e501-fc34061010a7" LABEL="ubuntu:0" TYPE="linux_raid_member" PARTUUID="451006ec-01"
/dev/sda5: UUID="8a79d5e6-f120-a0cf-fde5-107e237e2fcb" UUID_SUB="7a37e10b-ffb2-f1c7-7f68-5c2ec5860a28" LABEL="ubuntu:2" TYPE="linux_raid_member" PARTUUID="451006ec-05"
/dev/sda6: UUID="7285adee-cbc5-3247-ec01-52febebfb590" UUID_SUB="3cd7e3b2-3d84-44c4-fc53-b4055fde5876" LABEL="ubuntu:1" TYPE="linux_raid_member" PARTUUID="451006ec-06"
/dev/sdb1: UUID="975718c3-c315-01ea-3582-1c8a29349f1f" UUID_SUB="a7fda693-9403-d30d-4438-10be6f27c5df" LABEL="ubuntu:0" TYPE="linux_raid_member" PARTUUID="8c0d2ffe-01"
/dev/sdb5: UUID="8a79d5e6-f120-a0cf-fde5-107e237e2fcb" UUID_SUB="24456da0-442e-8ad2-1cbe-306edb58e2e6" LABEL="ubuntu:2" TYPE="linux_raid_member" PARTUUID="8c0d2ffe-05"
/dev/sdb6: UUID="7285adee-cbc5-3247-ec01-52febebfb590" UUID_SUB="77c91c14-f3e1-f4f9-9b4f-e603e2fdcd01" LABEL="ubuntu:1" TYPE="linux_raid_member" PARTUUID="8c0d2ffe-06"
/dev/sdc1: UUID="975718c3-c315-01ea-3582-1c8a29349f1f" UUID_SUB="e796e3e7-bba0-a979-0285-fe411cc0c3fe" LABEL="ubuntu:0" TYPE="linux_raid_member" PARTUUID="6b186cba-01"
/dev/sdc5: UUID="8a79d5e6-f120-a0cf-fde5-107e237e2fcb" UUID_SUB="42db3bd9-6024-b269-1e21-c23cc2f1d2d6" LABEL="ubuntu:2" TYPE="linux_raid_member" PARTUUID="6b186cba-05"
/dev/sdc6: UUID="7285adee-cbc5-3247-ec01-52febebfb590" UUID_SUB="f18ad01f-53de-0007-4e15-edb4cd9c2846" LABEL="ubuntu:1" TYPE="linux_raid_member" PARTUUID="6b186cba-06"
/dev/sdd5: UUID="8a79d5e6-f120-a0cf-fde5-107e237e2fcb" UUID_SUB="3d16d2cd-949b-c4fb-0929-8c8aa5d3daeb" LABEL="ubuntu:2" TYPE="linux_raid_member" PARTUUID="02ac51d3-05"

```

```
 
ubuntu@ubuntu:~$ lsblk
NAME   MAJ:MIN RM  SIZE RO TYPE MOUNTPOINT
loop0    7:0    0  1.5G  1 loop /rofs
sda      8:0    0  1.8T  0 disk 
&#9500;&#9472;sda1   8:1    0  487M  0 part 
&#9500;&#9472;sda2   8:2    0    1K  0 part 
&#9500;&#9472;sda5   8:5    0  7.5G  0 part [SWAP]
&#9492;&#9472;sda6   8:6    0  1.8T  0 part 
sdb      8:16   0  1.8T  0 disk 
&#9500;&#9472;sdb1   8:17   0  487M  0 part 
&#9500;&#9472;sdb2   8:18   0    1K  0 part 
&#9500;&#9472;sdb5   8:21   0  7.5G  0 part [SWAP]
&#9492;&#9472;sdb6   8:22   0  1.8T  0 part 
sdc      8:32   0  1.8T  0 disk 
&#9500;&#9472;sdc1   8:33   0  487M  0 part 
&#9500;&#9472;sdc2   8:34   0    1K  0 part 
&#9500;&#9472;sdc5   8:37   0  7.5G  0 part [SWAP]
&#9492;&#9472;sdc6   8:38   0  1.8T  0 part 
sdd      8:48   0  1.8T  0 disk 
&#9500;&#9472;sdd1   8:49   0  487M  0 part 
&#9500;&#9472;sdd2   8:50   0    1K  0 part 
&#9500;&#9472;sdd5   8:53   0  7.5G  0 part [SWAP]
&#9492;&#9472;sdd6   8:54   0  1.8T  0 part 
sde      8:64   1 14.6G  0 disk 
&#9492;&#9472;sde1   8:65   1 14.6G  0 part /cdrom
sr0     11:0    1 1024M  0 rom  

```

```

ubuntu@ubuntu:~$ sudo parted -l
Model: ATA ST2000DM001-1ER1 (scsi)
Disk /dev/sda: 2000GB
Sector size (logical/physical): 512B/4096B
Partition Table: msdos
Disk Flags: 

Number  Start   End     Size    Type      File system     Flags
 1      1049kB  512MB   511MB   primary                   boot, raid
 2      513MB   2000GB  2000GB  extended
 5      513MB   8511MB  7999MB  logical   linux-swap(v1)  raid
 6      8512MB  2000GB  1992GB  logical                   raid


Model: ATA ST2000DL003-9VT1 (scsi)
Disk /dev/sdb: 2000GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Disk Flags: 

Number  Start   End     Size    Type      File system     Flags
 1      1049kB  512MB   511MB   primary                   boot, raid
 2      513MB   2000GB  2000GB  extended
 5      513MB   8511MB  7999MB  logical   linux-swap(v1)  raid
 6      8512MB  2000GB  1992GB  logical                   raid


Model: ATA ST2000DL003-9VT1 (scsi)
Disk /dev/sdc: 2000GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Disk Flags: 

Number  Start   End     Size    Type      File system     Flags
 1      1049kB  512MB   511MB   primary                   boot, raid
 2      513MB   2000GB  2000GB  extended
 5      513MB   8511MB  7999MB  logical   linux-swap(v1)  raid
 6      8512MB  2000GB  1992GB  logical                   raid


Model: ATA ST2000DL003-9VT1 (scsi)
Disk /dev/sdd: 2000GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Disk Flags: 

Number  Start   End     Size    Type      File system     Flags
 1      1049kB  512MB   511MB   primary                   boot, raid
 2      513MB   2000GB  2000GB  extended
 5      513MB   8511MB  7999MB  logical   linux-swap(v1)  raid
 6      8512MB  2000GB  1992GB  logical                   raid


Model: Verbatim STORE N GO (scsi)
Disk /dev/sde: 15.6GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Disk Flags: 

Number  Start   End     Size    Type     File system  Flags
 1      1049kB  15.6GB  15.6GB  primary  fat32        boot, lba

```

Thanks,

Josh

---

### Post by darkod on 2017-10-19
Ok, so you do have mdadm sw raid and 3 raid arrays. From the same live mode try assembling all arrays it can detect:
```
sudo mdadm --verbose --assemble --scan
```

In case that works out check the arrays status:
```
cat /proc/mdstat
```

---

### Post by jphat on 2017-10-19
mdadm doesn't seem to work:
```

ubuntu@ubuntu:~$ sudo mdadm --verbose --assemble --scan
sudo: mdadm: command not found

```

2nd command returns:
```

ubuntu@ubuntu:~$ cat /proc/mdstat
Personalities : 
unused devices: <none>

```

---

### Post by darkod on 2017-10-20
Sorry, you have to add mdadm first when in a live session:
```
sudo apt-get install mdadm
```

If you restart the session, you have to do it again, it doesn't stay installed in a live session usually.

---

### Post by jphat on 2017-10-20
```

ubuntu@ubuntu:~$ sudo mdadm --verbose --assemble --scan
mdadm: looking for devices for /dev/md/0
mdadm: No super block found on /dev/sde1 (Expected magic a92b4efc, got 00000000)
mdadm: no RAID superblock on /dev/sde1
mdadm: No super block found on /dev/sde (Expected magic a92b4efc, got 00000000)
mdadm: no RAID superblock on /dev/sde
mdadm: /dev/sdd6 has wrong uuid.
mdadm: /dev/sdd5 has wrong uuid.
mdadm: /dev/sdd2 is too small for md: size is 2 sectors.
mdadm: no RAID superblock on /dev/sdd2
mdadm: No super block found on /dev/sdd (Expected magic a92b4efc, got 48c3c265)
mdadm: no RAID superblock on /dev/sdd
mdadm: /dev/sdc6 has wrong uuid.
mdadm: /dev/sdc5 has wrong uuid.
mdadm: /dev/sdc2 is too small for md: size is 2 sectors.
mdadm: no RAID superblock on /dev/sdc2
mdadm: No super block found on /dev/sdc (Expected magic a92b4efc, got 48c3c265)
mdadm: no RAID superblock on /dev/sdc
mdadm: /dev/sdb6 has wrong uuid.
mdadm: /dev/sdb5 has wrong uuid.
mdadm: /dev/sdb2 is too small for md: size is 2 sectors.
mdadm: no RAID superblock on /dev/sdb2
mdadm: No super block found on /dev/sdb (Expected magic a92b4efc, got 48c3c265)
mdadm: no RAID superblock on /dev/sdb
mdadm: /dev/sda6 has wrong uuid.
mdadm: /dev/sda5 has wrong uuid.
mdadm: /dev/sda2 is too small for md: size is 2 sectors.
mdadm: no RAID superblock on /dev/sda2
mdadm: No super block found on /dev/sda (Expected magic a92b4efc, got 48c3c265)
mdadm: no RAID superblock on /dev/sda
mdadm: cannot open device /dev/sr0: No medium found
mdadm: No super block found on /dev/loop0 (Expected magic a92b4efc, got 071c0a3e)
mdadm: no RAID superblock on /dev/loop0
mdadm: /dev/sdd1 is identified as a member of /dev/md/0, slot 3.
mdadm: /dev/sdc1 is identified as a member of /dev/md/0, slot 2.
mdadm: /dev/sdb1 is identified as a member of /dev/md/0, slot 1.
mdadm: /dev/sda1 is identified as a member of /dev/md/0, slot 0.
mdadm: added /dev/sdb1 to /dev/md/0 as 1
mdadm: added /dev/sdc1 to /dev/md/0 as 2
mdadm: added /dev/sdd1 to /dev/md/0 as 3
mdadm: added /dev/sda1 to /dev/md/0 as 0
mdadm: /dev/md/0 has been started with 4 drives.
mdadm: looking for devices for /dev/md/2
mdadm: No super block found on /dev/md/0 (Expected magic a92b4efc, got 0000003e)
mdadm: no RAID superblock on /dev/md/0
mdadm: No super block found on /dev/sde1 (Expected magic a92b4efc, got 00000000)
mdadm: no RAID superblock on /dev/sde1
mdadm: No super block found on /dev/sde (Expected magic a92b4efc, got 00000000)
mdadm: no RAID superblock on /dev/sde
mdadm: /dev/sdd6 has wrong uuid.
mdadm: /dev/sdd5 is busy - skipping
mdadm: /dev/sdd2 is too small for md: size is 2 sectors.
mdadm: no RAID superblock on /dev/sdd2
mdadm: /dev/sdd1 has wrong uuid.
mdadm: No super block found on /dev/sdd (Expected magic a92b4efc, got 48c3c265)
mdadm: no RAID superblock on /dev/sdd
mdadm: /dev/sdc6 has wrong uuid.
mdadm: /dev/sdc5 is busy - skipping
mdadm: /dev/sdc2 is too small for md: size is 2 sectors.
mdadm: no RAID superblock on /dev/sdc2
mdadm: /dev/sdc1 has wrong uuid.
mdadm: No super block found on /dev/sdc (Expected magic a92b4efc, got 48c3c265)
mdadm: no RAID superblock on /dev/sdc
mdadm: /dev/sdb6 has wrong uuid.
mdadm: /dev/sdb5 is busy - skipping
mdadm: /dev/sdb2 is too small for md: size is 2 sectors.
mdadm: no RAID superblock on /dev/sdb2
mdadm: /dev/sdb1 has wrong uuid.
mdadm: No super block found on /dev/sdb (Expected magic a92b4efc, got 48c3c265)
mdadm: no RAID superblock on /dev/sdb
mdadm: /dev/sda6 has wrong uuid.
mdadm: /dev/sda5 is busy - skipping
mdadm: /dev/sda2 is too small for md: size is 2 sectors.
mdadm: no RAID superblock on /dev/sda2
mdadm: /dev/sda1 has wrong uuid.
mdadm: No super block found on /dev/sda (Expected magic a92b4efc, got 48c3c265)
mdadm: no RAID superblock on /dev/sda
mdadm: cannot open device /dev/sr0: No medium found
mdadm: No super block found on /dev/loop0 (Expected magic a92b4efc, got 071c0a3e)
mdadm: no RAID superblock on /dev/loop0
mdadm: looking for devices for /dev/md/1
mdadm: No super block found on /dev/md/0 (Expected magic a92b4efc, got 0000003e)
mdadm: no RAID superblock on /dev/md/0
mdadm: No super block found on /dev/sde1 (Expected magic a92b4efc, got 00000000)
mdadm: no RAID superblock on /dev/sde1
mdadm: No super block found on /dev/sde (Expected magic a92b4efc, got 00000000)
mdadm: no RAID superblock on /dev/sde
mdadm: /dev/sdd5 has wrong uuid.
mdadm: /dev/sdd2 is too small for md: size is 2 sectors.
mdadm: no RAID superblock on /dev/sdd2
mdadm: /dev/sdd1 has wrong uuid.
mdadm: No super block found on /dev/sdd (Expected magic a92b4efc, got 48c3c265)
mdadm: no RAID superblock on /dev/sdd
mdadm: /dev/sdc5 has wrong uuid.
mdadm: /dev/sdc2 is too small for md: size is 2 sectors.
mdadm: no RAID superblock on /dev/sdc2
mdadm: /dev/sdc1 has wrong uuid.
mdadm: No super block found on /dev/sdc (Expected magic a92b4efc, got 48c3c265)
mdadm: no RAID superblock on /dev/sdc
mdadm: /dev/sdb5 has wrong uuid.
mdadm: /dev/sdb2 is too small for md: size is 2 sectors.
mdadm: no RAID superblock on /dev/sdb2
mdadm: /dev/sdb1 has wrong uuid.
mdadm: No super block found on /dev/sdb (Expected magic a92b4efc, got 48c3c265)
mdadm: no RAID superblock on /dev/sdb
mdadm: /dev/sda5 has wrong uuid.
mdadm: /dev/sda2 is too small for md: size is 2 sectors.
mdadm: no RAID superblock on /dev/sda2
mdadm: /dev/sda1 has wrong uuid.
mdadm: No super block found on /dev/sda (Expected magic a92b4efc, got 48c3c265)
mdadm: no RAID superblock on /dev/sda
mdadm: cannot open device /dev/sr0: No medium found
mdadm: No super block found on /dev/loop0 (Expected magic a92b4efc, got 071c0a3e)
mdadm: no RAID superblock on /dev/loop0
mdadm: /dev/sdd6 is identified as a member of /dev/md/1, slot 3.
mdadm: /dev/sdc6 is identified as a member of /dev/md/1, slot 2.
mdadm: /dev/sdb6 is identified as a member of /dev/md/1, slot 1.
mdadm: /dev/sda6 is identified as a member of /dev/md/1, slot 0.
mdadm: added /dev/sdb6 to /dev/md/1 as 1
mdadm: added /dev/sdc6 to /dev/md/1 as 2
mdadm: added /dev/sdd6 to /dev/md/1 as 3
mdadm: added /dev/sda6 to /dev/md/1 as 0
mdadm: /dev/md/1 has been started with 4 drives.
mdadm: looking for devices for /dev/md/2
mdadm: No super block found on /dev/md/1 (Expected magic a92b4efc, got 00000401)
mdadm: no RAID superblock on /dev/md/1
mdadm: No super block found on /dev/md/0 (Expected magic a92b4efc, got 0000003e)
mdadm: no RAID superblock on /dev/md/0
mdadm: No super block found on /dev/sde1 (Expected magic a92b4efc, got 00000000)
mdadm: no RAID superblock on /dev/sde1
mdadm: No super block found on /dev/sde (Expected magic a92b4efc, got 00000000)
mdadm: no RAID superblock on /dev/sde
mdadm: /dev/sdd6 has wrong uuid.
mdadm: /dev/sdd5 is busy - skipping
mdadm: /dev/sdd2 is too small for md: size is 2 sectors.
mdadm: no RAID superblock on /dev/sdd2
mdadm: /dev/sdd1 has wrong uuid.
mdadm: No super block found on /dev/sdd (Expected magic a92b4efc, got 48c3c265)
mdadm: no RAID superblock on /dev/sdd
mdadm: /dev/sdc6 has wrong uuid.
mdadm: /dev/sdc5 is busy - skipping
mdadm: /dev/sdc2 is too small for md: size is 2 sectors.
mdadm: no RAID superblock on /dev/sdc2
mdadm: /dev/sdc1 has wrong uuid.
mdadm: No super block found on /dev/sdc (Expected magic a92b4efc, got 48c3c265)
mdadm: no RAID superblock on /dev/sdc
mdadm: /dev/sdb6 has wrong uuid.
mdadm: /dev/sdb5 is busy - skipping
mdadm: /dev/sdb2 is too small for md: size is 2 sectors.
mdadm: no RAID superblock on /dev/sdb2
mdadm: /dev/sdb1 has wrong uuid.
mdadm: No super block found on /dev/sdb (Expected magic a92b4efc, got 48c3c265)
mdadm: no RAID superblock on /dev/sdb
mdadm: /dev/sda6 has wrong uuid.
mdadm: /dev/sda5 is busy - skipping
mdadm: /dev/sda2 is too small for md: size is 2 sectors.
mdadm: no RAID superblock on /dev/sda2
mdadm: /dev/sda1 has wrong uuid.
mdadm: No super block found on /dev/sda (Expected magic a92b4efc, got 48c3c265)
mdadm: no RAID superblock on /dev/sda
mdadm: cannot open device /dev/sr0: No medium found
mdadm: No super block found on /dev/loop0 (Expected magic a92b4efc, got 071c0a3e)
mdadm: no RAID superblock on /dev/loop0

```

And then:
```

ubuntu@ubuntu:~$ cat /proc/mdstat
Personalities : [raid10] 
md1 : active raid10 sda6[0] sdd6[3] sdc6[2] sdb6[1]
      3890141184 blocks super 1.2 512K chunks 2 near-copies [4/4] [UUUU]
      bitmap: 0/29 pages [0KB], 65536KB chunk

md0 : active raid10 sda1[0] sdd1[3] sdc1[2] sdb1[1]
      995328 blocks super 1.2 512K chunks 2 near-copies [4/4] [UUUU]
      
unused devices: <none>

```

---

### Post by darkod on 2017-10-20
OK, swap raid didn't get assembled because live mode is using swap partitions found on the disks, so mdadm skipped them as busy.

But md0 and md1 did get assembled, and it looks to me like that's your /boot and /. You can check this by mounting temporary at /mnt:
```
sudo mount /dev/md0 /mnt
ls /mnt
```

If it contains the kernels, that's your /boot device.

Then you can unmount it and mount md1 to take a peek:
```
sudo umount /mnt
sudo mount /dev/md1 /mnt
ls /mnt
```

One thing you wrote at the start is worrying me. You say it couldn't boot unless using older kernel. That is usually a sign of a problem. You shouldn't have left it like that...

You can try to chroot into the installation after assembling the raid from live mode, but even reinstalling the latest kernel maybe won't help because if there is another underlying issue the newest kernel might not boot you say.

The good thing is that at least mdadm seems to assemble the arrays correctly and in worst case you can use that to copy the data off the arrays to an external HDD, and then start over with the server.

Personally I think you are complicating your life with adding the GUI and driver for WiFi. Especially if you don't have much experience.

GUI seems like a nice option but actually controlling a server by CLI is not as complicated as it might sound. And it works much better, with the latest kernel instead of needing to use older ones. :)

As for WiFi, I would never put a server on a WiFi. In worst case, better to invest in WiFi extender with ethernet port, connect that to power outlet close to the server, connect it to your WiFi network and then connect the server by cable to it. The connection will be much more stable, and servers usually have no issues working with the ethernet ports, unlike with the wifi cards.

---

### Post by jphat on 2017-10-20
Forgot to add, after running:
```

sudo mdadm --verbose --assemble --scan

```
Two volumes suddenly pop up on the side bar, a 1Gb one with a grub folder in it and a 4 Tb one with what appears to be my data with everything still there!   I tried rebooting from the server but it still ends up at the initramfs prompt.

---

### Post by jphat on 2017-10-20
Sorry was sitting on page 1 when I last replied and didn't see your reply.

```

ubuntu@ubuntu:~$ sudo mount /dev/md0 /mnt
ubuntu@ubuntu:~$ ls /mnt
abi-4.4.0-87-generic                  memtest86+.bin
config-4.4.0-87-generic               memtest86+.elf
grub                                  memtest86+_multiboot.bin
initrd.img-4.4.0-87-generic           System.map-4.4.0-87-generic
initrd.img-4.4.0-87-generic.old-dkms  vmlinuz-4.4.0-87-generic
lost+found

```
The next group seems to load and show the folders:
```

ubuntu@ubuntu:~$ sudo umount /mnt
ubuntu@ubuntu:~$ sudo mount /dev/md1 /mnt
ubuntu@ubuntu:~$ ls /mnt
bin   dev   initrd.img.old  lost+found  opt   run   srv  usr
boot  etc   lib             media       proc  sbin  sys  var
core  home  lib64           mnt         root  snap  tmp  vmlinuz.old

```

Thanks for all the help.  I'm just going out for a while but have one or two more questions, mostly around whether this could be fixed from the current state? What made it go wrong in the first place and if I have to rebuild it what's the best method for setting it up for a RAID10 server?

When I did it there's loads of posts around but nothing covering the process from start to finish and seemingly no consensus as to the best way of doing it.

---

### Post by darkod on 2017-10-20
Yeah, I forgot you have a GUI so when you assemble the volumes they pop up on the sidebar and you can open them directly there.

Those are your /boot volume and your /.

We could try fixing from chroot, but it's not 100% sure it will work because I don't know what you have. To go into chroot (inside your OS installation from live mode) first unmount anything you might still have mounted in /mnt and then:
```
sudo umount /mnt
sudo mount /dev/md1 /mnt
sudo mount /dev/md0 /mnt/boot
sudo mount --bind /proc /mnt/proc
sudo mount --bind /sys /mnt/sys
sudo mount --bind /dev /mnt/dev
sudo chroot /mnt
```

From this moment on you are like inside your server OS installation. Anything you run is affecting the OS. First you can try simply updating the initramfs and update grub:

```
update-initramfs -u
update-grub
```

Exit the chroot, unmount what you mounted as preparation, and reboot:
```
exit   (now you are out of chroot)
sudo umount /mnt/dev
sudo umount /mnt/sys
sudo umount /mnt/proc
sudo umount /mnt/boot
sudo umount /mnt
```

Try to reboot and see if that helps.

---

### Post by jphat on 2017-10-20
Hi, I stopped at updating grub, see code below, it had some issue - should I still proceed?
```

root@ubuntu:/# update-initramfs -u
update-initramfs: Generating /boot/initrd.img-4.4.0-87-generic
root@ubuntu:/# update-grub
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-4.4.0-87-generic
Found initrd image: /boot/initrd.img-4.4.0-87-generic
Found memtest86+ image: /memtest86+.elf
Found memtest86+ image: /memtest86+.bin
  /run/lvm/lvmetad.socket: connect failed: No such file or directory
  WARNING: Failed to connect to lvmetad. Falling back to internal scanning.
done

```

---

### Post by darkod on 2017-10-20
Hmmm, you don't use LVM so it looks safe to continue. The important thing was that update-initramfs created new kernel image, in case there was any issue with that.

That update-grub warning looks safe to ignore at this moment.

---

### Post by jphat on 2017-10-20
Same again, goes back through the duplicated MD device name warnings and ends at initramfs again.

---

### Post by darkod on 2017-10-20
Lets try to get rid of the duplicated md devices, to make sure it is not creating an issue.

In live mode add mdadm package, assemble the arrays again and try modifying mdadm.conf:
```
sudo apt-get install mdadm
sudo mdadm --assemble --scan
sudo mount /dev/md1 /mnt
sudo nano /mnt/etc/mdadm/mdadm.conf
```

First lets try commenting out the group of 5 ARRAY enties (the ones you posted in first post). Just add # at the front of the line, then save the file with Ctrl+O and close the nano editor with Ctrl+X.

Then unmount /mnt and reboot the server. Check how it goes. In case you end up in initramfs again, copy here all messages and warning that you can. It might help knowing what actually the system is complaining about...

---

### Post by jphat on 2017-10-21
Gave it a quick try this morning, still same problem on reboot.  Just to confirm, to unmount the mounted /dev/md1 you'd use "sudo umount /dev/md1 /mnt"?

Thanks

---

### Post by darkod on 2017-10-21
Yes, although in umount it is allowed to use only one parameter because it is enough to know what to unmount. For example 'sudo umount /mnt'.

Any messages the initramfs prompt is giving you? It couldn't be complaining now about double md devices, there should be none.

---

### Post by jphat on 2017-10-23
Hi still the same error messages with duplicate MD device names ending with an ALERT! UUID=4d83... does not exist., as if it is referring to a different mdad.conf file.  I tried hashing out the other set of the ARRAYs so have done it both ways around.  Still the same.  Not sure what the significance is but it always refers to md/0 rather than md0.

---

### Post by darkod on 2017-10-23
md/0 and md0 are synonyms, that part should be an issue.

I don't see UUID starting with 4d83 related to any mdadm array. It can be that even with the array assembled the filesystem is missing or not detected. With the arrays assembled in live mode, can you try again the 'sudo blkid'? To see if it lists a filesystem from the array.

---

### Post by jphat on 2017-10-23
"blkid" does not show UUID 4d83.. anywhere?

---

