---
title: "Recommended RAID configurations?"
date: 2010-11-29
forum: Server Platforms
---

### Post by James78 on 2010-11-29
I'm running an Ubuntu Server with 3 RAID 0 drives. As someone else mentioned, this is extremely dangerous, and I already knew that but went along doing it anyways. I'd like to make my server more reliable by using a better RAID configuration, e.g. mirrored drives with RAID 1.

What RAID configurations would you recommend for a production server? As said earlier, I'm using 3 hard drives, and preferably I want redundancy for the data, and still being able to boot if one drive fails, things like that (most likely I'll be using RAID1 in the end as it looks good, however I'm not sure what to do with the 3rd drive). Please explain in detail! ;)

Oh, and if anyone has any ideas on how to convert 3 hard drives all in RAID 0 to your recommended setup, without loosing data of course, that would also be appreciated (I'm sure the Ubuntu Server's disc's rescue mode would be handy for this)

---

### Post by HugoSerrano on 2010-11-29
Hi!

You can use 2 drives in raid1 and the other to make backups. Or you can make a RAID5 with the 3 drives.

To do that you will have to copy your data to other place, make the raid 1 or 5 and copy back.

Regards!

---

### Post by James78 on 2010-11-29
> **HugoSerrano said:**
> Hi!

You can use 2 drives in raid1 **and the other to make backups**. Or you can make a RAID5 with the 3 drives.

To do that you will have to copy your data to other place, make the raid 1 or 5 and copy back.

Regards!
That would certainly help solve my dilemma of doing backups on the system drive. What I was doing was a bad idea since you want your backups to be safe in case of a system failure!

What should I do for the 3rd drive? Right now I'm thinking of 2 drives as RAID1, but still not sure what to do with the 3rd drive. I don't want it completely as filesystem backup, as I could do more with the drive (total 80GB).. Ideas?

Edit: "dd if=/dev/md0 of=/disk.iso" looks good for backing things up!

---

### Post by James78 on 2010-11-29
I think I'm going to go with RAID 5 to get all my drives used up. Performance (like RAID 0) + data protection (dedicated parity drive).

Since RAID 5 has degraded write performance though, I'd rather go with RAID 10 (1+0). Just like RAID 0, except mirrored onto another drive as well. Since no parity information needs to be calculated on writes, it's tons faster.

---

### Post by CharlesA on 2010-11-29
I haven't really noticed a huge amount of "degraded write performance" on my RAID5 array. My normal transfer speeds are between 70 and 110MB/sec. I'd say that's pretty decent since it's going over the network and not drive-to-drive.

If you wanted to get the most performance, you can just do RAID-0 and have a good backup.

---

### Post by James78 on 2010-11-29
RAID 0 would ordinarily be good, but I don't have another server to use as a secondary backup server, otherwise I'd go all for RAID 0.

Ya, I ended up doing RAID 5. Shouldn't be too bad, the only thing that frustrated me is that I have a 160GB, 120GB and a 80GB, and with the configuration I have 160GB md0 (mounted on /), and a 1.2GB swap, and that's it. Feels like a waste of hard drive potential, but at least my data will be safe.

---

### Post by CharlesA on 2010-11-29
I only RAID my data, not my OS. Running RAID with the OS on the drive is not worth it since you can always reinstall the OS.

---

### Post by James78 on 2010-11-29
I could always use some better ideas on how to RAID my drives. If you don't mind, how do you specifically do yours? I'm trying to figure out the best way to get the maximum usage out of all the drives, while maintaining crucial features like backups (mirror or parity) and whatnot. No configuration I've come across was able to get me very much data availability off of the drives while maintaining the backup feature of RAID.

I don't have a problem with not RAIDing the system itself, it's just that I'm a little worried if I don't have that part backed with RAID like the data, I'd loose my configuration data (BIND zones, FTP configuration, etc), and that's why I was RAIDing the whole / instead of just the data only. I might be able to get around this though because I have automatic periodic backups going to /var/backups, so I suppose I could just RAID /var and not the system.

---

### Post by kevinthecomputerguy on 2010-11-30
RAID5 is your very best bet.
 
But RAID5 wont boot as an operating system drive in most cases.
 
What you can do is partition all disks into 3 partitions
 
partition 1 disk 1 = 500 mb = /boot = ext2 (raid1)
partition 2 disk 1 = 1.5 x ram = swap (raid 5)
partition 3 disk 1 = rest-of-the-disk = ext3 (raid 5)
 
partition 1 disk 2 = 500 mb = /boot = ext2 (raid1)
partition 2 disk 2 = 1.5 x ram = swap (raid 5)
partition 3 disk 2 = rest-of-the-disk = ext3 (raid 5)
 
partition 1 disk 3 = 500 mb = /boot = ext2 (raid1)
partition 2 disk 3 = 1.5 x ram = swap (raid 5)
partition 3 disk 3 = rest-of-the-disk = ext3 (raid 5)
 
this way your /boot partition is raid 1 with 3 active. This is normally too much disk I\O, but the boot partition isnt ever written to, so you get 3 disks with identical grub (ideal !)
 
Then your swap and os are raid5, best mix of space and speed.
 
*note, If you have 2tb disks then you have to put /boot on a usb flash drive to keep the raid5 setup normal. But if you have 1.5tb or lower, you can use above partition scheme with no problems.
 
Anything less than raid5, or raid 1 with 3 active is a waste of time. *3 active is too much disk I\O except for /boot with is really used.
 
-Kev

---

### Post by James78 on 2010-11-30
Thanks for your configuration example! :) Just one question, why ext2 and ext3, why not just use ext4 for all of them?

---

### Post by kevinthecomputerguy on 2010-11-30
ext2 on /boot because you dont need a journaled fs for /boot
 
and ext3 on swap and /root file system because i live on the leading edge not the bleeding edge.
 
Sean Penn once was told... "no, lets walk down and efh them all"

---

### Post by James78 on 2010-11-30
I knew there was a reason for ext2 on the /boot, I figured it was a good one. Good idea with ext3 too, "stable not bleeding edge". Thanks for the explanations! :p

---

### Post by kevinthecomputerguy on 2010-11-30
I do what i can : - )
 
-KevinTheComputerGuy

---

### Post by CharlesA on 2010-11-30
Heh, mine's set up simpler then that:

320GB drive with the OS

3 x 2TB drives in RAID-5 for my data.

With drives of varing sizes, it gets a lot more complicated, unfortunately.

---

### Post by dtfinch on 2010-11-30
Between the 3 drives you could make 100gb, 60gb, and 20gb raid 1's. Then concatenate the 100 and 60gb raids into one 160gb with LVM for /home, and use the 20gb for /. That'd basically be a reinstall though. I don't have any suggestions for keeping your existing data though unless you have an extra drive. 1tb is pretty inexpensive these days.

---

