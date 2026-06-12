---
title: "unable to build mdadm raid 5"
date: 2008-11-30
forum: Server Platforms
---

### Post by malcomosx.chris on 2008-11-30
Hello

Im trying to build a raid 5 array from three 320GB (2x seagates, 1x WD) and one 300GB Maxtor.  The 4 drives are IDE and are connected to the computer via a IDE PCI controller.  The controller has 2 IDE channels, each support a primary and slave drive.  Each drive has a partition of 279.47GB.  I then issue the following commands.

#mdadm --create --verbose /dev/md0 --level=5 --raid-devices=4 /dev/sdb1 /dev/sdc1 /dev/sdd1 /dev/sde1 --auto=MD

I then use watch cat /proc/mdstat to view the creation of the array.  When its done i end up with this
```

Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md0 : active raid5 sdb[4](F) sde[5](F) sdd[6](F) sdc[7](F)
      879171840 blocks level 5, 64k chunk, algorithm 2 [4/0] [____]
      
unused devices: <none>
```

once the array has been created I then issue

# mdadm --detail /dev/md0 
```
mdadm: ARRAY line /dev/md0 has no identity information.
/dev/md0:
        Version : 00.90.03
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md0 : active raid5 sdb[4](F) sde[5](F) sdd[6](F) sdc[7](F)
      879171840 blocks level 5, 64k chunk, algorithm 2 [4/0] [____]
      # mdadm --detail --scan
mdadm: ARRAY line /dev/md0 has no identity information.
ARRAY /dev/md0 level=raid5 num-devices=4
unused devices: <none>
  Creation Time : Sun Nov 30 13:28:22 2008
     Raid Level : raid5
     Array Size : 879171840 (838.44 GiB 900.27 GB)
  Used Dev Size : 293057280 (279.48 GiB 300.09 GB)
   Raid Devices : 4
  Total Devices : 4
Preferred Minor : 0
    Persistence : Superblock is persistent

    Update Time : Sun Nov 30 22:59:57 2008
          State : clean, degraded
 Active Devices : 0
Working Devices : 0
 Failed Devices : 4
  Spare Devices : 0

         Layout : left-symmetric
     Chunk Size : 64K

    Number   Major   Minor   RaidDevice State
       0       0        0        0      removed
       1       0        0        1      removed
       2       0        0        2      removed
       3       0        0        3      removed

       4       8       16        -      faulty spare   /dev/sdb
       5       8       64        -      faulty spare   /dev/sde
       6       8       48        -      faulty spare   /dev/sdd
       7       8       32        -      faulty spare   /dev/sdc
```

# mdadm --detail --scan
mdadm: ARRAY line /dev/md0 has no identity information.
ARRAY /dev/md0 level=raid5 num-devices=4

I have zero'd out each hard drive, they all function on there own
I am unable do gain any smart data from smartctl from the hard drives
I have also tried building the array with the drives in reverse order
Finally i have tried reading the drives back in

---

### Post by fjgaude on 2008-12-01
Say, after you created the array did you place a filesystem on it?

```
sudo mkfs -t ext3 /dev/md0
```

Like that?

---

### Post by obg123 on 2008-12-01
Either way, it shouldn't say that all drives are failed (F).

It might be that you are using 4 units on only 2 IDE ports. Everybody recommends against that. However, I would be a bit surprised if it caused this serious problem. Then again, it might...

---

### Post by fjgaude on 2008-12-01
I also note that the array was created using names like /dev/sdb1. Such is not the same /dev/sdb. That could be an issue.

---

### Post by malcomosx.chris on 2008-12-01
Hello, thanks for the reply :)

I have tried formating the raid array using mkfs.ext3 /dev/md0 and with the -f flag as well.

I have also tried building the array on the drives not using partitions (ie /dev/sdb dev/sdc)

Chris

---

### Post by albandy on 2008-12-01
have you defined the partitions as raid before creating it with the command mdadm?

else fdisk every partition and change the partition type to fd

for example:

to change sdb1 to raid:
sudo fdisk /dev/sdb
t
1
fd
w

now sdb1 is a raid type partition

---

### Post by malcomosx.chris on 2008-12-01
Hello

I used gparted flag manager to activate the raid flag and to format the partitions on each drive.

Chris

---

### Post by albandy on 2008-12-01
and have you defined the /etc/mdadm.conf file?

read this manual:
[http://www.linuxhomenetworking.com/wiki/index.php/Quick_HOWTO_:_Ch26_:_Linux_Software_RAID](http://www.linuxhomenetworking.com/wiki/index.php/Quick_HOWTO_:_Ch26_:_Linux_Software_RAID)

It may help you a lot.

---

### Post by malcomosx.chris on 2008-12-01
Hello

yes i believe i have by issuing the following commands

# echo "DEVICE partitions" > /etc/mdadm/mdadm.conf
# mdadm --detail --scan >> /etc/mdadm/mdadm.conf

Chris

---

### Post by fjgaude on 2008-12-01
Okay, have you looked at the mdadm.conf file to see if it reads like it should, with the right UUID, drives, etc?

---

### Post by malcomosx.chris on 2008-12-02
hello

the uuid is in there and i have also followed the information at [http://tldp.org/HOWTO/Software-RAID-HOWTO-5.html](http://tldp.org/HOWTO/Software-RAID-HOWTO-5.html).  i have also removed the mdadm.conf file and ran the reassemble command.

chris

---

### Post by fjgaude on 2008-12-03
Okay, can you show us what the mdadm.conf file has in it?

---

### Post by doogy2004 on 2008-12-03
Here is a set of instructions that I created:

Create Raid Array with LVM2 Volume Inside

[LIST]
[*]Determine the Logical location of all drives to be included in array.
sudo lshw -short | grep "/dev/"
[*]Zero all drives to be included in array
sudo shred -vfz -n 0 /dev/sdd
[*]Restart Computer so that the kernel sees the changes.
[*]Format all drives to be included in array.
sudo fdisk /dev/sdd
[LIST]
[*]Delete all partitions from the drive.
[*]Create a new primary partition with the default size (default is the entire disk).
[*]Change partition type to "Linux raid auto"
[*]Write Changes to Drive
[*]Repeat for each disk that will be included in the array.
[/LIST]
[*]Restart Computer so that the kernel sees the changes.
[*]Determine the Logical locations of all drives to be included in the array again to verify if any have changed.
[*]Create the Raid device (if you have a missing drive replace it with "missing")
sudo mdadm --create --verbose /dev/md0 --level=5 --raid-devices=3 /dev/sdd1 /dev/sde1 /dev/sda1
[*]Wait for the array to build.  You can check the progress with:
sudo mdadm --detail /dev/md0
cat /proc/mdstat
[*]Restart computer to confirm the Configuration.
ls /dev/ | grep "md"
[*]Create physical volume.
sudo pvcreate /dev/md0
[*]Create the volume group.  Replace XXX with (Megabytes of array)/65,000, then round to next number (2,4,8,16,32,64,128,256,...).
sudo vgcreate -s XXXM lvm-raid /dev/md0
[*]Create the logical volume.
sudo lvcreate -l 100%VG lvm-raid -n lvm0
[*]Confirm creation of logical volume.
sudo lvdisplay /dev/lvm-raid/lvm0
[*]Format the logical volume.
sudo mkfs.ext3 /dev/lvm-raid/lvm0
[*]Mount the volume
sudo mkdir /media/lvm0
sudo mount /dev/lvm-raid/lvm0 /media/lvm0
[*]Confirm that the volume is mounted.
df -h /media/lvm0
[/LIST]

---

### Post by malcomosx.chris on 2008-12-04
Hello

thanks for the reply

I'll try your how to when i get a chance

Chris

---

