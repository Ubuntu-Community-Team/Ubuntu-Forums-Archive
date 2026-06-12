---
title: "Server no longer work i have connected a raid 1 hard drive need help access lvm2 pv"
date: 2016-06-23
forum: Server Platforms
---

### Post by jcer93705 on 2016-06-23
Hey guys. I have a qnap nas server. There is a lvm2 pv partition that I wanna access so I can back up the files. The nas screwed up
on me. Here more info in the pic. I'm using Ubuntu 16.04. Is there also a way I can convert it to ntfs? Ty

---

### Post by MAFoElffen on 2016-06-24
Just by a quick glance, I am assuming that this sdb, was a sole disk in your NAS(?), sdb1 & sdb2 were a mirror RAID1(?) and sbb3 was your LVM PV(?) And this is as-seen from your rescue system. Was this the sole, root-disk of your NAS?

What I would do is to mount the filesystems of sdb1, 2 & 3... and (optionally) chroot into the system on it. if successful, then you could read anything on it and back it off onto other media. As RAID1 (since they are a mirror), you would only have to treat either sb1 or sb2 as a single volume... to get the lvm info to mount sdb3 as an lvm device.

For instance, as a query to collect info for you to do your mounts...
```

sudo /sbin/sfdisk -l /dev/sdb >> ~/Documents/results.txt 
sudo /sbin/pvscan >> ~/Documents/results.txt 
sudo /sbin/vgscan >> ~/Documents/results.txt 
sudo /sbin/lvscan >> ~/Documents/results.txt 

```
Then copy the text of that results.txt within code tags in a post here.

---

