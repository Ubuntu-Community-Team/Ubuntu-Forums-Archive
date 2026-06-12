---
title: "How to tell which physical disk = which device in mdadm?"
date: 2011-05-16
forum: Server Platforms
---

### Post by sailor420 on 2011-05-16
I have an mdadm-based RAID 5 array, and recently realized that were a given disk to die, I'm not sure I'd be able to identify which physical disk needed to be replaced.

Is there any way to determine which physical disk corresponds to which device (e.g. /dev/sda), short of unplugging them one at a time?

Wishing I'd paid better attention when I built the array :oops:

---

### Post by dtfinch on 2011-05-16
"hdparm -I /dev/sda" should tell you the serial number of sda. Then you'd look for the drive with that serial printed on it. Or if you can't access it to check, you'd check the serials of all the other drives.

---

### Post by rubylaser on 2011-05-16
If you don't know for sure, one way is to use smartctl to look at the serial #, it will match the serial # on the drive label.
```
sudo apt-get install smartmontools
```
like this...
```
root@fileserver:~# smartctl -d ata -a /dev/sdb | grep Serial
Serial Number:    9TE07BS0
root@fileserver:~# smartctl -d ata -a /dev/sdc | grep Serial
Serial Number:    WD-WMATV1391142

```

Or use sdparm, or hdparm :)
```
root@fileserver:~# hdparm -I /dev/sdb | grep Serial | head -n1
```

---

### Post by sailor420 on 2011-05-16
This is *exactly* what I was looking for. Many thanks!

---

