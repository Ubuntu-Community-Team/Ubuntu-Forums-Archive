---
title: "how to map/predict physical SATA ports to device IDs?"
date: 2009-01-05
forum: Server Platforms
---

### Post by ljwobker on 2009-01-05
working through a new file server with all the joys that RAID and LVM bring -- not new to unix but new to the file system admin side... so I have what may be a dumb question:

I have a Foxconn G43MX motherboard which has six onboard SATA connectors.  Is there any way to {predict, identify, control} how these physical ports are mapped to device names?  

Asked another way, can I know for certain that "SATA 1" on the mobo will *always* be /dev/sda ?    Along the same lines, if I pull a drive from "SATA 1" and plug it back into "SATA 3" -- what happens?  (assume for now it's NOT the boot drive, but one of my RAID elements)

Basically, I've gotten to the point where I at least somewhat understand the abstractions between block devices, partitions, LVM:vg, LVM:pv, LVM:lv, mountpoints, directories, files, etc...  but I need help with the actual motherboard SATA-to-linux device ID mappings.

thanks...

---

### Post by ljwobker on 2009-01-06
bump?  seems so simple.  ;-(

---

### Post by Vegan on 2009-01-06
They should map in the same order as the physical ports on the motherboard unless you change the boot order in the BIOS.

Check you motherboard manual for the port numbers relative to the board placement.

---

### Post by logos34 on 2009-01-06
> **ljwobker said:**
> 
Asked another way, can I know for certain that "SATA 1" on the mobo will *always* be /dev/sda ?    Along the same lines, if I pull a drive from "SATA 1" and plug it back into "SATA 3" -- what happens?  (assume for now it's NOT the boot drive, but one of my RAID elements)

drive letters hardly matter anymore, as ubuntu now uses the UUID system exclusively to find/designate disk partitions--to see what I mean check your /etc/fstab and /boot/grub/menu.lst.  You'll still see '/dev/sda' or whatever in /boot/grub/device.map, but that's just a list of the config at the time of installation, doesn't affect boot.  It's in fstab too but just a description (i.e. '**#** /dev/sda1')

However in general the letters should be assigned alphabetically starting with lowest channel, so channel sata0 is a, sata1 or higher is b etc.  Kind of like IDE used to be, where hda was primary master, hdb primary slave, hdc secondary master, hdd secondary slave

---

### Post by ljwobker on 2009-01-07
OK, I'm starting to get the hang of this UUID thing.  A bit confusing at first, but the benefits are immediately obvious as you get into more complex builds.... 

I was messing around with various filesystems and LVM operations and got myself a new, separate partition built for /home and successfully moved the old /home data to that.  I could explicitly mount the filesystem by doing "mount -a" with this line in /etc/fstab: 

```
/dev/vg0/lv0   /home   ext3    defaults,errors=remount-ro   0  2
```


but if I tried to mount via UUID, it would NOT work.... 
```

UUID=f40f5c1e-7671-43cf-b239-6f1292eac340 /home   ext3  defaults,errors=remount-ro   0   2

vkg-filer1:/dev/disk/by-uuid# mount -a
mount: special device /dev/disk/by-uuid/f40f5c1e-7671-43cf-b239-6f1292eac340 does not exist


```


I managed to determine that this was because the various links in /dev/disk/by-uuid were NOT set up correctly until I rebooted...  before reboot:
```
lwobker@vkg-filer1:/dev/disk/by-uuid$ ls -al
lwobker@vkg-filer1:/dev/disk/by-uuid$ ls -lgo
total 0
lrwxrwxrwx 1 10 2009-01-06 21:47 2403910e-0cd3-41f4-b731-8e238debf706 -> ../../sda5
lrwxrwxrwx 1 10 2009-01-06 21:47 b90c3b8c-0c47-4e82-ae93-5e84d1d3c0c8 -> ../../sda1
```


after reboot:```
lwobker@vkg-filer1:/dev/disk/by-uuid$ ls -al
lwobker@vkg-filer1:/dev/disk/by-uuid$ ls -lgo
total 0
lrwxrwxrwx 1 10 2009-01-06 21:47 2403910e-0cd3-41f4-b731-8e238debf706 -> ../../sda5
lrwxrwxrwx 1 10 2009-01-06 21:47 b90c3b8c-0c47-4e82-ae93-5e84d1d3c0c8 -> ../../sda1
lrwxrwxrwx 1 20 2009-01-06 21:47 f40f5c1e-7671-43cf-b239-6f1292eac340 -> ../../mapper/vg0-lv0

```

So clearly SOMETHING is re-generating all the links in the "by-uuid" directory.... but I'll be damned if I can figure out what that is.  If I can figure it out, then when I generate new volumes in LVM I can do it myself.  I suppose that I could manually add the entries into the **/dev/disk/by-uuid** directory, but that seems like it's a hack and might break things (duplicate entries when the auto-generator runs maybe?)

anyone happen to know what might be regenerating these?

---

### Post by ljwobker on 2009-01-07
Blessed google.  Took me a couple hours to find the exact search, but yielded this:

[http://ubuntuforums.org/showthread.php?t=430123](http://ubuntuforums.org/showthread.php?t=430123)

> Originally Posted by **Ralph Corderoy** 					[[IMG]http://ubuntuforums.org/images/buttons/viewpost.gif[/IMG]]("http://ubuntuforums.org/showthread.php?p=4803061#post4803061") 				
 				*`sudo /etc/init.d/udev restart' works. It makes udev work through the block devices again and /dev/disk/by-uuid gets up to date.*


---

