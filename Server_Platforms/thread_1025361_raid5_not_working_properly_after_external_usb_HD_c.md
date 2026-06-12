---
title: "raid5 not working properly after external usb HD connected to 2.6.22-14.47-server"
date: 2008-12-30
forum: Server Platforms
---

### Post by noskillzaz on 2008-12-30
Hello,
Sorry if I don't include the pertinent information, I'm a bit linux stupid at this point. I have a raid 5 setup on 2.6.22-14.47-server, that has been running for almost a year now. Unfortunately, I decided to try to connect an external USB Hard Drive to copy some of the data off, and the next thing you know, my RAID decided to disappear on me.

this is a 7x320G RAID5 configuration, using LVM and reiserfs.

Showing the following for the current status of the raid, and it appears some drives are now missing after a few reboots:

```

Every 0.1s: cat /proc/mdstat                            Mon Dec 29 23:18:38 2008

Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [ra
id10]
md0 : inactive sdd1[1](S) sda1[6](S) sdc1[5](S) sdg1[4](S) sde1[2](S) sdb1[0](S)
      1875411456 blocks

unused devices: <none>

```

When trying to add the missing device... sdf1:
```

sudo mdadm --manage /dev/md0 --add /dev/sdf1
mdadm: cannot get array info for /dev/md0

```

Seeing the following errors on bootup as well in the /var/log/messages file:
```

Dec 29 23:12:17 sloth kernel: [  708.529078] md: array md0 already has disks!
Dec 29 23:12:17 sloth kernel: [  708.537235] md: array md0 already has disks!
Dec 29 23:12:17 sloth kernel: [  708.548692] md: array md0 already has disks!
Dec 29 23:12:17 sloth kernel: [  708.557699] md: array md0 already has disks!
Dec 29 23:12:17 sloth kernel: [  708.565576] md: array md0 already has disks!

```

Any help would be appreciated, in trying to recover this without losing my data.

Thanks in advance.

---

### Post by Cracauer on 2008-12-30
mdadm --stop /dev/md0
mdadm --assemble /dev/md0 /dev/sda1 /dev/sdd1 [all drives]

This probably was probably caused by the disk controller driver issuing a couple read errors while the kernel was integrating the USB subsystem.

---

### Post by noskillzaz on 2008-12-30
I had attempted that and kept getting an error message stating that md0 was not in the conf file.

At one time I was able to examine and get the UUID:

</var/log> sudo mdadm --examine --scan /dev/sd[a-g]1
ARRAY /dev/md0 level=raid5 num-devices=7 UUID=cc2d67ad:7a64c56d:a75a6b75:d2ec3ebb

Once I got this, I added this back into the /etc/mdadm/mdadm.conf file.

I was then able to activate the raid, but one drive was missing. Once I added that back into md0, it looks like my raid is now recovering.
</shares/documents> sudo lvs
  LV        VG   Attr   LSize   Origin Snap%  Move Log Copy% 
  documents vg0  -wi-ao  40.00G                              
  movies    vg0  -wi-ao   1.37T                              
  mp3s      vg0  -wi-ao 150.00G                              
  nntp      vg0  -wi-ao 100.00G                              
  photos    vg0  -wi-ao 100.05G  

just remounted the drives, and voila!

sudo mount -a

---

### Post by Cracauer on 2008-12-30
> **noskillzaz said:**
> I had attempted that and kept getting an error message stating that md0 was not in the conf file.


Glad you are running.

For the record, the lines I gave you don't use the config file.  They would have brought the array up no matter how screwed up the config file is.

---

