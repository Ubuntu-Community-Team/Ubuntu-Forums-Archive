---
title: "Replacing a 'hot spare' in a RAID 1 configuration"
date: 2015-09-23
forum: Server Platforms
---

### Post by redadept on 2015-09-23
Hello --

/dev/sda on our 4-year old Ubuntu RAID 1 server (md0 / swap and md1 /boot) just failed -- and because I had installed a spare (/dev/sdc) when creating the array, mdadm apparently jumped right in and rebuilt the array automatically on /dev/sdb and /dev/sdc.  /proc/mdstat now shows:

```
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10]
md0 : active raid1 sdb1[1] sdc1[2]
      14324 blocks super 1.2 [2/2] [UU]

md1 : active raid1 sdb2[1] sdc2[2]
      976745336 blocks super 1.2 [2/2] [UU]

unused devices: <none>
```

I am now getting a daily email telling me of a "SparesMissing" event, which is correct now that the spare has been used. What I would like to do is replace the failed sda drive with a new spare, slotted in as sda instead of the old sdc, ready to jump in again should either RAID drive fail.  I *think* I know the steps, but since this is a production server, I would like to be absolutely sure I know what I'm doing, and I have not found any exact walkthroughs that detail how to replace / format / add / sync a hot spare in a RAID 1 system.  Any help / tutorial links would be greatly appreciated, including step-by-steps for such things as "plug in a new drive and partition it for the RAID array".  The server is running under Ubuntu 14.04.3 LTS.

Thank you in advance.

---

### Post by darkod on 2015-09-23
If I'm not mistaken all you need to do is --add the new partition as member of the array. It will automatically take the "spare" slot.

In fact, I think that even if you had no spares in the original configuration, when your array has all the members present and you add one more, it turns itself into a spare. Because an array will never change the number of members (devices) by itself. You do that manually with the --grow option. So when you add one more member it's spare.

---

### Post by redadept on 2015-09-24
Thank you Darko -- after reading several posts and articles on creating a spare, it seems that there is a bit more work to do.  I would appreciate knowing from anyone who is following this thread if these steps are complete / accurate:

(Note that I have identified the RAID array as using disks with MBR partitions, and because we are currently running on a spare server, I can shut down the production computer)

1. Remove the drive from the RAID array.

```
sudo mdadm --manage /dev/md0 --remove /dev/sda1
sudo mdadm --manage /dev/md0 --remove /dev/sda2
```

2. Shut down the system.

(Will this cause GRUB to automatically change /dev/sdb and /dev/sdc to /dev/sda and /deb/sdb??)

3. Remove the SATA drive cable, then the power cable. Mount the new drive and connect the power cable.  Wait 10 seconds, then connect the drive cable.

4. Identify the new drive and the device name -- hopefully it will slot in as /dev/sda

**(Would appreciate if someone would verify that the following is correct)**

5. Copy the partitioning setup from one of the good drives in the existing array to the new spare drive:

```
sudo sfdisk -d /dev/sdb | sfdisk /dev/sda
```

(Do I need to randomize the guid of the new spare after copying the partition scheme?  If so, is this possible with sfdisk? Should the spare be formatted / partitioned using a different method?)

6. Make the new partitioned spare bootable

```
sudo grub-install /dev/sda
```

7. Add the new drive to the RAID array

```
sudo mdadm --manage /dev/md0 --add /dev/sda1
sudo mdadm --manage /deb/md1 --add /dev/sda2
```

Check (?? how ??) to verify that the bootable spare is now installed in the RAID array and will function as planned in the event of a main drive failure.

Thanks again to any who can help.

---

### Post by darkod on 2015-09-24
1. You only need to --remove a partition if it shows as member of the array. From the cat output it didn't seem so. You can check more details about an array with:
```
sudo mdadm --detail /dev/md1
```

Does it show sda2 in there?

2-4. Upon boot the BIOS reads the SATA slots in their order, low to high. So if you replace sda with a new disk connected to the same SATA port and without booting before installing the new disk, the new one should stay sda too.

5. You can copy the partitioning layout or simply create manually identical partitions as on the other disks. Your choice.

6-7. This is the main part, similar to what I said. Just add the new partitions to the corresponding arrays. In the --detail output it will show sda1 and sda2 as spares for md0 and md1.

---

### Post by redadept on 2015-09-28
Thank you Darko -- I have a replacement disk on order, and will let you know how the install goes ...

---

### Post by redadept on 2015-09-29
Hello Darko --

I have installed the spare 1TB drive as discussed, and the process seems to have gone smoothly.  If I cat /proc/mdstat I see
```
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md1 : active raid1 sda2[3](S) sdb2[1] sdc2[2]
      976745336 blocks super 1.2 [2/2] [UU]
      
md0 : active raid1 sda1[3](S) sdb1[1] sdc1[2]
      14324 blocks super 1.2 [2/2] [UU]

``` and mdadm --detail for both md0 and md1 shows a spare enabled for both.  If I use fdisk to look at /dev/sda I get:
```
Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            2048       30719       14336   fd  Linux raid autodetect
/dev/sda2   *       30720  1953523711   976746496   fd  Linux raid autodetect

```
which also looks good.  Is there anything else I should check?

Again, thank you for the guidance.

-- Darrell

---

### Post by darkod on 2015-09-29
It looks good. You again have spare in both arrays. I think that's it.

---

