---
title: "software raid issue"
date: 2016-08-12
forum: Server Platforms
---

### Post by evertmdc on 2016-08-12
Hello everyone,

I'm having an issue with one of my machines where I had a software raid 1 ( I guess ) on two [COLOR=#575757][FONT=arial]ADATA Premier Pro SP900, 256 GB SSD drives.
[/FONT][/COLOR]One of the drives died and my system began sending messages like this
```
lk_update_request: I/O error, dev sdb, sector 1400976

 sd 2:0:0:0: [sdb] tag#13 FAILED Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
```

The system was not usable anymore and I decided to reboot.

Result:
The system does not want to boot anymore and complains that it cannot find a lvm uuid.
When using a live cd I can see one disk id fd, Linux raid autodetect.
The second disk is dead.

I tried recovering using this:
```
fsck.ext4 -f -c -v /dev/sda1
```
but that said 'is in use' even though it was not mounted.

Assuming it was due to the raid I did the following:
```
[COLOR=#000000][FONT=monospace]mdadm --examine --scan[/FONT][/COLOR]
```
Who gave me one array back. It printed /dev/md/0 instead of /dev/md0 I see in the examples but apparently that should not be an issue.

Then I did an assemble
```
mdadm --assemble /dev/md/0
```
And a fsck on the resulting disk but it did not work either.

Then later I read that on a raid 1 you can just mount  the disk as ext4 since it should be the same but that didn't work.

**So my questions**, what is the good way to recover from a software raid 1 failure and why did it affect my system in the first place?
Should I do an update grub and will my system boot then?
Should I have done the following instead of rebooting?

```
mdadm --manage --set-faulty /dev/md0 /dev/sdb1
```

---

### Post by darkod on 2016-08-12
First post the output of this:
```
sudo mdadm --assemble --scan
sudo mdadm -D /dev/md0   (assuming the array assembles again as md0)
sudo mdadm --examine /dev/sda1
```

PS. The LVM you mentioned, do you have it on top of the raid1 array? In theory, a raid1 with one failed member should have kept on working... There is another issue obviously. Maybe one disk failed earlier only temporarily and the array was actually working only from sdb without you noticing, so now when sdb failed it all failed...

---

### Post by SeijiSensei on 2016-08-12
I've found that I can mount one of the disks in a RAID1 array as a normal ext4 filesystem.  So if /dev/sdb1 and /dev/sdc1 form the array, and sdb1 fails, I can use
```
sudo mount -t ext4 /dev/sdc1 /mnt/point
```
to mount the device normally.  Your use of LVM may take this option off the table though.

---

### Post by evertmdc on 2016-08-16
Hello,

Well, it seems like I accidentally put it on a raid0. That's a bummer.
How come the array state is marked 'AA'? I'm working here on a second machine with the disk plugged in through a USB disk enclosure.

```
sudo mdadm --examine /dev/sde1
/dev/sde1:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x0
     Array UUID : 6b102fb4:ed7ad42b:089962fc:68ac296b
           Name : machine:0
  Creation Time : Tue May 17 10:42:16 2016
     Raid Level : raid0
   Raid Devices : 2


 Avail Dev Size : 499853312 (238.35 GiB 255.92 GB)
    Data Offset : 262144 sectors
   Super Offset : 8 sectors
          State : clean
    Device UUID : 84625ca6:e796f867:7ca4934a:00ab9405


    Update Time : Tue May 17 10:42:16 2016
       Checksum : 4bc07cc4 - correct
         Events : 0


     Chunk Size : 512K


   Device Role : Active device 1
   Array State : AA ('A' == active, '.' == missing)




```

---

### Post by darkod on 2016-08-16
This looks like a newly created array. Look how the Events are at 0. It also says it's clean and like you noticed, AA. So this is not a degraded array or something...

Depending which commands you were running you might have created raid0 over your raid1, we can only assume here not having the information. In case you created new array but did not format it or mounted it yet, you might still be able to save the underlaying raid1. Assuming you really did have raid1 originally...

PS. Since you seem to be surprised too, are you sure the sde disk is the correct one? Because using enclosures the drive letters might not be in the order you expect them... Don't forget that.

---

### Post by evertmdc on 2016-08-16
Hello Darkod,

I did play around with the partition type yes altough I only  used mdadm examine and assemble commands from what I recall.
How would I be able to get my data off the disk should there still be a raid 1 under there?

The disk is correct since I checked all disks before plugging this one in. Only 'sde' was added with the timestamp of when it was plugged in.

Thanks

---

### Post by darkod on 2016-08-16
First lets get one thing straight, that you never replied to. What's with the LVM message you mentioned in your first post and that I asked about? Did you have LVM in the original setup or not? And if you did, did it involve the raid1 array you are trying to recover?

Because it makes a difference whether it was included in LVM or not. In such case probably best to be working on the original machine, to put the disk back.

On the other hand, if it was only mdadm without LVM, you can work on another machine without problems and we can try recovering the array.

---

### Post by evertmdc on 2016-08-22
Hello Darkod,

Sorry for not responding sooner.
Yes there was LVM on top of the raid array. It did involve the raid1 array I'm trying to recover.

I assume I made a mistake when installing and had a raid 0 instead of raid 1, so the data is lost.

The machine is currently reinstalled with only mdadm in raid 1 for the system disks for sake of simplicity when recovering.. The data disks are still on lvm though.

---

