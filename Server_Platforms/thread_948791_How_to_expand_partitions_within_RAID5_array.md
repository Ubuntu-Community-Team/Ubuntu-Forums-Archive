---
title: "How to expand partitions within RAID5 array"
date: 2008-10-15
forum: Server Platforms
---

### Post by ShiftyPowers on 2008-10-15
Hey guys, i posted this in the Tutorials forum, but probably makes more sense to put it here as a separate item.

Question for all you RAID knowledgeable peeps out there. I just finished creating my first RAID5 array out of 3 x 1TB WD Caviar drives. The problem was that I had a lot of data that I could not get rid of before creating the array. So what I did is that on each drive I created two partitions, say sda1 (100G) and sda2 (900G). I spread my existing data over the 3x100G partitions and was left with 3x900G blank partitions.

I created a new RAID5 array on the 3x900G partitions and put an lvm logical volume on top of it running ext3.

I then transferred all the data from the 3x100G partitions into the RAID array.

So far so good.

Now what I want to do is expand my RAID array to include the 3x100G paritions which are now empty.

Can that be done easily? Is there a way to EXPAND the underlying partitions that make up the raid array (i.e. make each 900G partition, 1TB)? or do I just add the 3x100G partitions as separate drives to the existing array (so that the array will have 6 partitions underneath it)?

Thanks for your help,
Shifty
ShiftyPowers is online now Report Post   	Edit/Delete Message

---

### Post by ShiftyPowers on 2008-10-16
figured it out so for posterity I will put this here:

[http://michael-prokop.at/blog/2006/09/09/raid5-online-resizing-with-linux/]("http://michael-prokop.at/blog/2006/09/09/raid5-online-resizing-with-linux/")

the relevant code is:

```
# Initiate a RAID5 setup for testing purposes:
mdadm --create --verbose /dev/md0 --level=5 --raid-devices=3 /dev/hda1 /dev/hdb1 /dev/hdd1

# Create filesystem, mount md0, create a testfile and save md5sum for later check:
mkfs.ext3 /dev/md0
mount /dev/md0 /mnt/test
dd if=/dev/urandom of=/mnt/test/dd bs=512 count=10000
md5sum /mnt/test/dd > md5sum

# Make sure the RAID is synched via checking:
cat /proc/mdstat

# Now remove one partition:
mdadm /dev/md0 --fail /dev/hdd1 --remove /dev/hdd1

# Delete partition, create a new + bigger one and set partition type to fd (Linux raid autodetect):
cfdisk /dev/hdd

# And re-add the partition:
mdadm -a /dev/md0 /dev/hdd1

# Make sure the RAID is synched via checking:
cat /proc/mdstat

# Repeat the steps for all other disks/partitions as well:
mdadm /dev/md0 --fail /dev/hdb1 --remove /dev/hdb1
cfdisk /dev/hdb
mdadm -a /dev/md0 /dev/hdb1
cat /proc/mdstat
mdadm /dev/md0 --fail /dev/hda1 --remove /dev/hda1
cfdisk /dev/hda
mdadm -a /dev/md0 /dev/hda1
cat /proc/mdstat

```

and 

```
root@grml ~ # mdadm --detail /dev/md0 | grep -e 'Array Size' -e 'Device Size'
     Array Size : 390912 (381.81 MiB 400.29 MB)
    Device Size : 195456 (190.91 MiB 200.15 MB)
root@grml ~ # mdadm --grow /dev/md0 -z max
root@grml ~ # mdadm --detail /dev/md0 | grep -e "Array Size" -e 'Device Size'
     Array Size : 976512 (953.79 MiB 999.95 MB)
    Device Size : 488256 (476.89 MiB 499.97 MB)

```

---

### Post by ShiftyPowers on 2008-10-16
double post

---

### Post by fjgaude on 2008-10-16
So to make a bigger array but not increase the number of drives you take one out at a time and then add the bigger one back in.

I would never have thought of that. I would have just created a bigger array with the new drives. I guess that is why I **always have current backups**, one online, one near-line, and one offline.

---

### Post by ShiftyPowers on 2008-10-16
yeah, it's a pretty clever solution.  just takes a long time because everytime you take out a drive and added back you have to wait for the array to resync.  
But at least it should solve the issue for people that don't have enough backup space to move all their data offline while creating a brand new array.

---

