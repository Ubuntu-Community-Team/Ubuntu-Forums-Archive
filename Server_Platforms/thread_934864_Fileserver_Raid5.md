---
title: "Fileserver Raid5"
date: 2008-10-01
forum: Server Platforms
---

### Post by mwerlberger on 2008-10-01
Hi,

I'm building a little fileserver with 3xTB disks with an epia board and a small chenbro server case. Everything assembled now and ready for install. Now there is the question if i should use a seperate 2.5" HDD for the main system (will be ubuntu server i think) and have the 3 raid disks mounted as software raid5. The other idea is to install the os directly onto the raid5 array.

Is that even possible or what are the main disadvantages. The main advantage is that the epia has 'only' 4 Sata ports and there will be an upgrade with a 4th HDD for the raid array if space gets a problem.

The final idea is to buy a Raid controller and use this one to manage the raid5 array and have the 2.5" SATA disk as main os hdd. Of course the most robust solution i think but it is the most expensive also...

Finally i will provide a howto for setting up ubuntu server with a raid5 array in the wiki due to the lack of something like that.

Thanks for any help,
 Manuel

---

### Post by Krupski on 2008-10-01
> **mwerlberger said:**
> Hi,

I'm building a little fileserver with 3xTB disks with an epia board and a small chenbro server case. Everything assembled now and ready for install. Now there is the question if i should use a seperate 2.5" HDD for the main system (will be ubuntu server i think) and have the 3 raid disks mounted as software raid5. The other idea is to install the os directly onto the raid5 array.

Is that even possible or what are the main disadvantages. The main advantage is that the epia has 'only' 4 Sata ports and there will be an upgrade with a 4th HDD for the raid array if space gets a problem.

The final idea is to buy a Raid controller and use this one to manage the raid5 array and have the 2.5" SATA disk as main os hdd. Of course the most robust solution i think but it is the most expensive also...

Finally i will provide a howto for setting up ubuntu server with a raid5 array in the wiki due to the lack of something like that.

Thanks for any help,
 Manuel

Sounds like you're building a file server just like the kind I made! (mine is even in a small Chenbro desktop case!).

Anyway, here's what I would suggest:

Get a COMPACT FLASH to IDE adapter card. Get a 4 GB compact flash camera card. Partition the CF 1/2-1/2 (2GB Linux, 2GB swap). Install Server on the CF card. A full Ubuntu Server install takes up only about 700 MB and a 2GB swapspace is more than enough.

```

root@storage:/# df -H
Filesystem             Size   Used  Avail Use% Mounted on
/dev/sda1              2.0G   690M   1.2G  37% /         **[COLOR="Red"]<--- compact flash[/COLOR]**
varrun                 4.2G   189k   4.2G   1% /var/run
varlock                4.2G      0   4.2G   0% /var/lock
udev                   4.2G    41k   4.2G   1% /dev
devshm                 4.2G      0   4.2G   0% /dev/shm
/dev/md0              1986G   444G  1542G  22% /home/shared

```

Then, use your 3 hard drives SOLELY as a RAID-5 storage device... not one drop of Linux on them.

That way, your system will always boot, no matter what happens to your RAID array.

If you're interested, here's a link for the CF-to-IDE adapter board:

[http://www.addonics.com/products/flash_memory_reader/adebidecf.asp](http://www.addonics.com/products/flash_memory_reader/adebidecf.asp)


Good luck!

-- Roger

---

