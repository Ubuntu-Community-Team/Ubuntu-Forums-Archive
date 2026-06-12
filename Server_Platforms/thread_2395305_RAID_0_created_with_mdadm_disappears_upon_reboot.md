---
title: "RAID 0 created with mdadm disappears upon reboot"
date: 2018-06-29
forum: Server Platforms
---

### Post by drewbuntu2 on 2018-06-29
Hi folks, after following along through several RAID setup walkthroughs I keep having the same problem: immediately after setting up what looks like a working RAID 0 array with two disks, I reboot and the RAID completely disappears.  Any help is much appreciated.

In my most recent attempt, I generally try to follow the process suggested at [https://www.digitalocean.com/community/tutorials/how-to-create-raid-arrays-with-mdadm-on-ubuntu-16-04](https://www.digitalocean.com/community/tutorials/how-to-create-raid-arrays-with-mdadm-on-ubuntu-16-04). As some background, I am currently using ubuntu 16.04 LTS, and I am often updating this system with new hard drives (at some point in the past I did have a working RAID array setup). The drive with the OS, swap file, and boot sector is not involved in any of this (that's on a single drive which I'm not messing around with). Here is the process I'm trying:

First I confirm that no RAID devices are currently recognized:
```
~>cat /proc/mdstat
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
unused devices: <none>
```

Then I examine my current disk setup:
```
~>lsblk -o NAME,SIZE,FSTYPE,TYPE,MOUNTPOINT
NAME     SIZE FSTYPE TYPE MOUNTPOINT
sda    931,5G        disk 
&#9500;&#9472;sda1   512M vfat   part /boot/efi
&#9500;&#9472;sda2 899,1G ext4   part /
&#9492;&#9472;sda3  31,9G swap   part [SWAP]
sdb      2,7T        disk 
&#9492;&#9472;sdb1   2,7T ext4   part 
sdc      7,3T        disk 
&#9492;&#9472;sdc1   7,3T ext4   part /media/drew/external
sdd      2,7T        disk 
&#9492;&#9472;sdd1   2,7T ext4   part 
sde      2,7T        disk 
&#9492;&#9472;sde1   2,7T ext4   part 
sdf      1,8T        disk 
sdg      1,8T        disk 
```

sda is my main drive with the OS, sdc is an external USB drive, and sdb sdd and sde are additional drives that aren't involved. I would like to assemble sdf and sdg in a RAID 0 device. I create the array using mdadm and then check /proc/mdstat again. As I do this step I notice that mdadm indicates the disks show evidence of already being part of a RAID array - I assume this is a remnant of my previous attempts to put these disks into a RAID array, although it seems peculiar to me that they didn't show up as RAIDed disks in my previous steps.
```
~>sudo mdadm --create --verbose /dev/md0 --level=0 --raid-devices=2 /dev/sdf /dev/sdg

mdadm: chunk size defaults to 512K
mdadm: /dev/sdf appears to be part of a raid array:
       level=raid0 devices=0 ctime=Wed Dec 31 21:00:00 1969
mdadm: partition table exists on /dev/sdf but will be lost or
       meaningless after creating array
mdadm: /dev/sdg appears to be part of a raid array:
       level=raid0 devices=0 ctime=Wed Dec 31 21:00:00 1969
mdadm: partition table exists on /dev/sdg but will be lost or
       meaningless after creating array
Continue creating array? Y

~>cat /proc/mdstat
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md0 : active raid0 sdg[1] sdf[0]
      3906766848 blocks super 1.2 512k chunks
```

Next I create the file system. This next step takes a minute or so.
```
~>sudo mkfs.ext4 -F /dev/md0
```

Then I set up the mount point, mount it, and check the status:
```
~>sudo mkdir -p /home/drew/partyverse
~>sudo mount /dev/md0 /home/drew/partyverse

~>df -h -x devtmpfs -x tmpfs
Filesystem      Size  Used Avail Use% Mounted on
/dev/sda2       885G  149G  692G  18% /
/dev/sda1       511M  3,5M  508M   1% /boot/efi
/dev/sdc1       7,3T  3,6T  3,3T  53% /media/drew/external
/dev/md0        3,6T   68M  3,4T   1% /home/drew/partyverse
```

Then I update the mdadm.conf file, initramfs, and fstab:
```
~>sudo mdadm --detail --scan | sudo tee -a /etc/mdadm/mdadm.conf
~>sudo update-initramfs -u
~>echo '/dev/md0 /home/drew/partyverse ext4 defaults,nofail,discard 0 0' | sudo tee -a /etc/fstab
```

As far as I understand that should be all I need to do. Before rebooting I take one more look at the status of things:
```
~>lsblk -o NAME,SIZE,FSTYPE,TYPE,MOUNTPOINT
NAME     SIZE FSTYPE            TYPE  MOUNTPOINT
sda    931,5G                   disk  
&#9500;&#9472;sda1   512M vfat              part  /boot/efi
&#9500;&#9472;sda2 899,1G ext4              part  /
&#9492;&#9472;sda3  31,9G swap              part  [SWAP]
sdb      2,7T                   disk  
&#9492;&#9472;sdb1   2,7T ext4              part  
sdc      7,3T                   disk  
&#9492;&#9472;sdc1   7,3T ext4              part  /media/drew/external
sdd      2,7T                   disk  
&#9492;&#9472;sdd1   2,7T ext4              part  
sde      2,7T                   disk  
&#9492;&#9472;sde1   2,7T ext4              part  
sdf      1,8T linux_raid_member disk  
&#9492;&#9472;md0    3,7T ext4              raid0 /home/drew/partyverse
sdg      1,8T linux_raid_member disk  
&#9492;&#9472;md0    3,7T ext4              raid0 /home/drew/partyverse

~>cat /proc/mdstat
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md0 : active raid0 sdg[1] sdf[0]
      3906766848 blocks super 1.2 512k chunks
      
unused devices: <none>
```
That all looks OK. Furthermore the array is showing up on the unity desktop launcher on the left. So now I go ahead and reboot. Upon startup it seems that all my progress is gone. The array no longer shows up on the desktop launcher, and here are my current /proc/mdstat and lsblk statuses:
```
~>lsblk -o NAME,SIZE,FSTYPE,TYPE,MOUNTPOINT
NAME     SIZE FSTYPE TYPE MOUNTPOINT
sda    931,5G        disk 
&#9500;&#9472;sda1   512M vfat   part /boot/efi
&#9500;&#9472;sda2 899,1G ext4   part /
&#9492;&#9472;sda3  31,9G swap   part [SWAP]
sdb      2,7T        disk 
&#9492;&#9472;sdb1   2,7T ext4   part 
sdc      2,7T        disk 
&#9492;&#9472;sdc1   2,7T ext4   part 
sdd      2,7T        disk 
&#9492;&#9472;sdd1   2,7T ext4   part 
sde      1,8T        disk 
sdf      1,8T        disk 
sdg      7,3T        disk 
&#9492;&#9472;sdg1   7,3T ext4   part /media/drew/external
~>cat /proc/mdstat
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
unused devices: <none>
```

For what it's worth, here is my fstab file (there are lots of lines commented out from previous RAID attempts):
```
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda2 during installation
UUID=be98ffd1-0d57-4b15-a0f5-a2e782738ec1 /               ext4    errors=remount-ro 0       1
# /boot/efi was on /dev/sda1 during installation
UUID=DDE0-CAE0  /boot/efi       vfat    umask=0077      0       1
# swap was on /dev/sda3 during installation
UUID=21d53db4-9e6e-4924-aa08-ac537d6ffb25 none            swap    sw              0       0
# /dev/md0    /home/drew/multiverse    ext4    defaults    0    0
#/dev/sde1   /home/drew/partyverse    ext4    defaults    0    0
#/dev/md0 /home/drew/multiverse ext4 defaults,nofail,discard 0 0
#/dev/md0 /home/drew/multiverse  ext4 defaults,nofail,discard 0 0
#/dev/md0 /home/drew/partyverse ext4 defaults,nofail,discard 0 0
/dev/md0 /home/drew/partyverse ext4 defaults,nofail,discard 0 0
```

and here is my mdadm.conf file (again a few lines commented out):
```

#ARRAY /dev/md0 metadata=1.2 UUID=f0fb916c:cdac7d5c:9ed585c2:b67b9545
#ARRAY /dev/md/0  metadata=1.2 UUID=ce7b7885:62514a3b:3e0bb2e9:a0d206af name=ALMA-data-cruncher:0
ARRAY /dev/md0 metadata=1.2 name=ALMA-data-cruncher:0 UUID=f35233e6:e1a5e6fa:c7fb6c1a:c8956a0a
```

Any insight would be much appreciated!!

---

### Post by oldfred on 2018-06-29
Moved to the server sub-forum where those who know more about RAID my look.

Normally RAID 0 is not recommended.
       Don't bother with RAID 0 unless you have a specific need for speed without data redundancy, since if one drive goes out, you lose the whole array.
[http://en.wikipedia.org/wiki/RAID](http://en.wikipedia.org/wiki/RAID)
[http://www.smallnetbuilder.com/nas/nas-features/31745-data-recovery-tales-raid-is-not-backup](http://www.smallnetbuilder.com/nas/nas-features/31745-data-recovery-tales-raid-is-not-backup)

---

### Post by darkod on 2018-06-29
1. I would use partitions, not whole disks. You use sdf and sdg to create the array, when it's better to use partitions like sdf1 and sdg1. Remove current array (if any), create one single big partition on the disks, and create new raid0 array.

2. After that, please post the output of the following:
```
sudo blkid
cat /etc/mdadm/mdadm.conf | grep ARRAY
```

---

### Post by drewbuntu2 on 2018-06-29
Thanks for the move. And that's a good point - in this case I do indeed have a specific need for disk i/o speed (specifically sequential reads and writes). The data redundancy issue is an unfortunate side effect, but I'm aware of it and taking appropriate precautions.

---

### Post by drewbuntu2 on 2018-06-29
Wow, that... that worked! Thanks darkod! In case you still want to know, the results of that code are:
```

~>sudo blkid
[sudo] password for drew: 
/dev/sda1: UUID="DDE0-CAE0" TYPE="vfat" PARTLABEL="EFI System Partition" PARTUUID="02283d1c-50e7-439d-b77d-4d035693ae24"
/dev/sda2: UUID="be98ffd1-0d57-4b15-a0f5-a2e782738ec1" TYPE="ext4" PARTUUID="ac5aac4a-1425-4e50-8993-43e415843e72"
/dev/sda3: UUID="21d53db4-9e6e-4924-aa08-ac537d6ffb25" TYPE="swap" PARTUUID="5b0b14c8-0a7f-47f1-aeab-be4190035f72"
/dev/sdb1: UUID="9f3ee418-951f-4d59-a457-62b73e048ae4" TYPE="ext4" PARTLABEL="sdb1" PARTUUID="c15e5952-a27f-4f85-b23f-9f5c4f8e4f77"
/dev/sdc1: UUID="b85703e3-a20a-4118-9289-4ac986684063" TYPE="ext4" PARTLABEL="sdc1" PARTUUID="c2e60402-7092-46cc-b321-b8c7f8b82c2f"
/dev/sdd1: UUID="44cf5329-263f-44c4-a4fb-8ab990227fb1" TYPE="ext4" PARTLABEL="Basic data partition" PARTUUID="527b4977-c607-475e-b19a-0c6c45a3694d"
/dev/sde1: LABEL="external" UUID="f20e9782-9ce8-4502-b127-1335559f653d" TYPE="ext4" PARTLABEL="My Book" PARTUUID="0ca89f31-ce2b-4011-9cc4-559603aa2cb5"
/dev/sdf1: UUID="1a790af3-467e-c2e4-ca88-9efbc79d4333" UUID_SUB="d04674b0-c898-a0ab-ee3d-c6eb68bc9f92" LABEL="ALMA-data-cruncher:0" TYPE="linux_raid_member" PARTUUID="049759b3-1781-445f-9c39-029666ac117b"
/dev/sdg1: UUID="1a790af3-467e-c2e4-ca88-9efbc79d4333" UUID_SUB="65e9d81a-f482-d23d-02bb-c2cba951d952" LABEL="ALMA-data-cruncher:0" TYPE="linux_raid_member" PARTUUID="69ada397-49d7-4b30-b794-f0dc7a5b9cd6"
/dev/md0: UUID="6198d20d-84a9-4f37-82fd-0ce7a23fa756" TYPE="ext4"
~>cat /etc/mdadm/mdadm.conf | grep ARRAY
#ARRAY /dev/md0 metadata=1.2 UUID=f0fb916c:cdac7d5c:9ed585c2:b67b9545
#ARRAY /dev/md/0  metadata=1.2 UUID=ce7b7885:62514a3b:3e0bb2e9:a0d206af name=ALMA-data-cruncher:0
#ARRAY /dev/md0 metadata=1.2 name=ALMA-data-cruncher:0 UUID=f35233e6:e1a5e6fa:c7fb6c1a:c8956a0a
ARRAY /dev/md0 metadata=1.2 name=ALMA-data-cruncher:0 UUID=1a790af3:467ec2e4:ca889efb:c79d4333
```

---

### Post by darkod on 2018-06-30
Glad it worked. Cheers.

---

