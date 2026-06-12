---
title: "create an encrypted RAID 6 array from the ground up"
date: 2012-01-26
forum: Server Platforms
---

### Post by alfonso78 on 2012-01-26
A full howto on how to create and tune a RAID 6 with 4 disks (using 4k sectors) and LUKS (for encryption)

why RAID 6? because [http://en.wikipedia.org/wiki/RAID_5_write_hole](http://en.wikipedia.org/wiki/RAID_5_write_hole)

why encrypted? cause it's bad enough if somebody steals my hw, but for sure I'd freak out if they get my data

[COLOR="Red"]NOTE NOTE NOTE
most of these commands are descructive. 
Don't follow the guide if you have no idea of what you are doing
or you might end up rewriting other disks...[/COLOR]

some basics:
for my system my 4 disks are /dev/sdb /dev/sdc /dev/sdd /dev/sde
change everything according to your configuration

-------START OF THE SECTION FOR PEOPLE WHO HAD PREVIOUS RAID-------

First of all of a few commands in case you are "redoing" your RAID:
(the cleanup instructions come from here:
[http://www.tcpdump.com/kb/os/linux/removing-raid-devices.html](http://www.tcpdump.com/kb/os/linux/removing-raid-devices.html))

```
cat /proc/mdstat
```

(use the correct md from cat /proc/mdstat)

```
sudo mdadm -S /dev/md127
```

you can check from /proc/mdstat if your existing RAID uses partitions
(e.g. sdb1) or block devices (e.g. sdb)

```
sudo mdadm --zero-superblock /dev/sdb
```
or
```
sudo mdadm --zero-superblock /dev/sdb1
```

and then repeat for each element of the array as listed in /proc/mdstat

Remove the DEVICE and ARRAY entry's associated with the array from /etc/mdadm.conf
Remove the array from /etc/fstab

and reboot (at least I did. It's prob not necessary).

if everything went well, you type cat /proc/mdstat and you get this:

```
$ cat /proc/mdstat
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5]
[raid4] [raid10]
unused devices: <none>
```

-------END OF THE SECTION FOR PEOPLE WHO HAD PREVIOUS RAID-------

now let's start from the basics: fdisk. if you have 4k sectors disks, you want to partition them correctly.
you correctly partitioned your disks when each partions start at a multiple of 8 (or 4, I'm not sure).

bad partitioning:

```
# fdisk -l /dev/sdb

Disk /dev/sdb: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x22cf0cdc

  Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              63  3907024064  1953512001   fd  Linux raid autodetect

```
good partitioning:

```
# fdisk -l /dev/sdb

Disk /dev/sdb: 2000.4 GB, 2000398934016 bytes
81 heads, 63 sectors/track, 765633 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x22cf0cdc

  Device Boot      Start         End      Blocks   Id  System
/dev/sdb1            2048  3907029167  1953513560   fd  Linux raid autodetect

```
apparently nowadays the default settings for fdisk will play nice with
4k sectors disks, but anyway it's easy to verify with the above
command.

also remember to set the right ID for the partition (fd)

now you want to create your RAID (make sure you use the correct
devices for your case). Notice we use partitions (sdb1) and not block device (sdb) in the command.

```
$ sudo mdadm --verbose --create /dev/md0 --level 6 --chunk 64 --raid-devices 4 /dev/sd[b-e]1
mdadm: layout defaults to left-symmetric
mdadm: layout defaults to left-symmetric
mdadm: layout defaults to left-symmetric
mdadm: layout defaults to left-symmetric
mdadm: layout defaults to left-symmetric
mdadm: layout defaults to left-symmetric
mdadm: size set to 1953512384K
mdadm: Defaulting to version 1.2 metadata
mdadm: array /dev/md0 started.
```

you might ask, why chunks of 64? Cause I read it in this very nice blog: [http://louwrentius.com/blog/category/raid/](http://louwrentius.com/blog/category/raid/)

as you can see md is already started syncing your RAID without you doing anything except creating the array:

```
$ cat /proc/mdstat
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10]
md0 : active raid6 sde1[3] sdd1[2] sdc1[1] sdb1[0]
     3907024768 blocks super 1.2 level 6, 64k chunk, algorithm 2 [4/4] [UUUU]
     [>....................]  resync =  0.0% (1292736/1953512384)
finish=1821.5min speed=17862K/sec

unused devices: <none>
```

but you can notice the very low speed...

I'm not sure why the synching speed was so slow, but that is really not the read/write performance of the system

In fact I'm not sure yet if that speed is meaningful cause

hdparm -tT /dev/md0 shows a different story compare to /proc/mdstat:

```
# hdparm -tT /dev/md0

/dev/md0:
 Timing cached reads:   7362 MB in  2.00 seconds = 3683.27 MB/sec
 Timing buffered disk reads: 608 MB in  3.00 seconds = 202.36 MB/sec
```
 
for a thread specifically about tuning read: [http://ubuntuforums.org/showthread.php?p=11642898](http://ubuntuforums.org/showthread.php?p=11642898)

Now we have to create /etc/mdadm/mdadm.conf

```
echo "DEVICE partitions" > /etc/mdadm/mdadm.conf
echo "HOMEHOST fileserver" >> /etc/mdadm/mdadm.conf
echo "MAILADDR  youruser@gmail.com" >> /etc/mdadm/mdadm.conf
mdadm --detail --scan >> /etc/mdadm/mdadm.conf
```

to make sure you receive emails from mdadm, follow this:
[http://zackreed.me/articles/39-send-system-email-with-gmail-and-ssmtp](http://zackreed.me/articles/39-send-system-email-with-gmail-and-ssmtp)
I actually use an incredibly more complicated way (since I didn't know
this article then).
If the first method doesn't work for you, try this:
[http://ubuntuforums.org/showthread.php?t=1866284](http://ubuntuforums.org/showthread.php?t=1866284)

Now I move on to set an encryption layer on the md device.

I don't know if you need the sync to wait, but I did.

here I will follow this howto and other pages I found online:
[http://www.g-loaded.eu/2005/11/10/encrypt-devices-using-dm-crypt-and-luks/](http://www.g-loaded.eu/2005/11/10/encrypt-devices-using-dm-crypt-and-luks/)

so first you need to initialize your md device with random data
this is a security precaution. In theory you can skip it, but if you 
want an encrypted file system I don't think you will

```
dd if=/dev/urandom of=/dev/md0
```

And here we are, at the encryption level.

I tried for days to find a decent howto that would explain parameters of cryptsetup without luck,
so I stick with the default.

```
sudo cryptsetup --verbose --verify-passphrase luksFormat /dev/md0
# "storage" can be any string that makes sense to you
sudo cryptsetup luksOpen /dev/md0 storage
sudo mkfs.ext4 /dev/mapper/storage
sudo mount /dev/mapper/storage /storage
```

apparently you can even use the presence of a usb key as passphrase:
[http://binblog.info/2008/12/04/using-a-usb-key-for-the-luks-passphrase/](http://binblog.info/2008/12/04/using-a-usb-key-for-the-luks-passphrase/)

then remember to make a backup of the headers:

```
cryptsetup luksHeaderBackup /dev/md0 --header-backup-file ./backup.img
```

in case you'll need to restore you can use:

```
cryptsetup luksHeaderRestore /dev/md0 --header-backup-file ./backup.img
```

now before you finish, add a bitmap to your RAID (to speed up
rebuilding after a crash or after removing/adding a device):

```
mdadm --grow --bitmap=internal /dev/md0
```

maintenance: set your system (via cron or anacron) 
to check your data once in a while (once a week?)

```
echo check >> /sys/block/md0/md/sync_action
```

finally add this in grub:
```
GRUB_CMDLINE_LINUX="bootdegraded=true" 
```

to make sure it doesn't hang when you boot your system 
with a degraded RAID array

other useful links:
Mdadm Cheat Sheet: [http://www.ducea.com/2009/03/08/mdadm-cheat-sheet/](http://www.ducea.com/2009/03/08/mdadm-cheat-sheet/)
some mdadm tutorials: [http://zackreed.me/articles?tag_id=22](http://zackreed.me/articles?tag_id=22)
tune RAID: [http://www.cyberciti.biz/tips/linux-raid-increase-resync-rebuild-speed.html](http://www.cyberciti.biz/tips/linux-raid-increase-resync-rebuild-speed.html)

---

### Post by rubylaser on 2012-01-26
Looks good from just a casual look.  The only thing I did notice is your intro about the write hole in RAID5.  RAID6 can suffer from a similar problem, when two disks don't match the others in the array. This can happen if the power is cut  in the middle of a full stripe write.  

The only way to avoid this is to do an atomic write, meaning it's completed or not done at all. Hardware RAID cards have a battery backed write cache so that even if power is cut off, they can complete their writes.  ZFS allows for this with it's copy-on-write (btfrs supports this as well), but mdadm arrays not do support this.  A good UPS is really the best way to mitigate this potential shortcoming in mdadm.  I just thought I'd pass that along.

---

### Post by alfonso78 on 2012-01-27
> **rubylaser said:**
> Looks good from just a casual look.  The only thing I did notice is your intro about the write hole in RAID5.  RAID6 can suffer from a similar problem, when two disks don't match the others in the array. This can happen if the power is cut  in the middle of a full stripe write.  

The only way to avoid this is to do an atomic write, meaning it's completed or not done at all. Hardware RAID cards have a battery backed write cache so that even if power is cut off, they can complete their writes.  ZFS allows for this with it's copy-on-write (btfrs supports this as well), but mdadm arrays not do support this.  A good UPS is really the best way to mitigate this potential shortcoming in mdadm.  I just thought I'd pass that along.

yes, sure! thank you! This is exactly why I write my learning: to learn even more! ;-)

thanks for sharing!

---

### Post by Cheesemill on 2012-01-27
Instead of going for RAID6 with 4 drives I'd go for RAID10 instead.

You'll end up with the same capacity but it will be a lot faster as there is no need for parity calculations.

---

### Post by alfonso78 on 2012-01-27
Maybe I'm wrong, but I think RAID 10 is a terrible (terrible) choice. Since if you are really unlucky you might end up losing half of your data if you loose the wrong 2 disks (see bold in the quote).

From [http://en.wikipedia.org/wiki/RAID:](http://en.wikipedia.org/wiki/RAID:)
> RAID 1+0: (a.k.a. RAID 10) mirrored sets in a striped set (minimum four drives; even number of drives) provides fault tolerance and improved performance but increases complexity.
The key difference from RAID 0+1 is that RAID 1+0 creates a striped set from a series of mirrored drives. **The array can sustain multiple drive losses so long as no mirror loses all its drives.**[8]

with RAID 6 I can loose any two disks.

---

### Post by Cheesemill on 2012-01-27
If I was going for an array with a large number of drives then I would definately go for RAID6, but with only 4 then the chances of losing the wrong 2 would still only half the MTBF of your array.

Bearing in mind that RAID should never be a backup solution, only a business continuity plan I still think that I'd choose RAID10 with 4 drives for the extra performance / lower CPU cost.

As always though it's up to the individual to weigh up the pro's and con's of a solution.

---

### Post by alfonso78 on 2012-01-27
True and I agree with you.

I just wanted to make clear that the best performance comes at a cost.

And it's not a cost I'm willing to pay, especially since I get more than 200MB/sec in reading AND writing with cheap green HDs...

Not sure why I would need more than that since it's already more than a Gbit network could handle.

but indeed, anyone has different needs.

cheers,

---

### Post by rubylaser on 2012-01-27
> **alfonso78 said:**
> True and I agree with you.

I just wanted to make clear that the best performance comes at a cost.

And it's not a cost I'm willing to pay, especially since I get more than 200MB/sec in reading AND writing with cheap green HDs...

Not sure why I would need more than that since it's already more than a Gbit network could handle.

but indeed, anyone has different needs.

cheers,

The other thing to consider is with mdadm you cannot currently grow a RAID10 array, but a RAID6 has no problem adding disks down the line.  For a home server, I've always went with RAID6.  It's a good tradeoff for redundancy + capacity.

---

### Post by drdos2006 on 2012-01-28
Kevinthecomputerguy has put up a couple of nice videos on setting up raid at [http://www.woodel.com](http://www.woodel.com)  as well.

regards

---

