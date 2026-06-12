---
title: "Swap old system into new system without reinstalling?"
date: 2011-08-13
forum: Server Platforms
---

### Post by GriFF3n on 2011-08-13
I currently have a server running 10.04.3 and am upgrading the system, ie new motherboard/CPU/Ram. Is it possible to throw the old hard drive into the new system and still have everything work? I've setup quite a bit of config files and I don't want to have to do it again if possible. Any suggestions? Thanks!

---

### Post by GriFF3n on 2011-08-14
Bump for some advice.

---

### Post by ian dobson on 2011-08-14
Hi,

You should be able to just swap the harddisk to the new server. The only problem you could have is with the network card. As the mac address changes udev will think it's a new network device and create a new ethX device. You'll need to edit your /etc/network/interfaces and add/change your ethX device.

What you could do is use dd to duplicate your boot drive to another drive then boot/test the new server.

Regards
Ian Dobson

---

### Post by GriFF3n on 2011-08-14
Thank you sir, will give this a try. 

> **ian dobson said:**
> Hi,

You should be able to just swap the harddisk to the new server. The only problem you could have is with the network card. As the mac address changes udev will think it's a new network device and create a new ethX device. You'll need to edit your /etc/network/interfaces and add/change your ethX device.

What you could do is use dd to duplicate your boot drive to another drive then boot/test the new server.

Regards
Ian Dobson

---

### Post by GriFF3n on 2011-08-14
I was able to swap in the 2 hard drives and boot to the main drive, so no need to install or config anything! All I had to do was update interfaces like you said Ian. Much appreciated! Only problem I am getting is "Disk /dev/sdb doesn't contain a valid partition table". I had fstab auto mount sdb in the original server. I commented it out and for some reason I keep getting this error when using fdisk. Any ideas?

---

### Post by ian dobson on 2011-08-14
> **GriFF3n said:**
> I was able to swap in the 2 hard drives and boot to the main drive, so no need to install or config anything! All I had to do was update interfaces like you said Ian. Much appreciated! Only problem I am getting is "Disk /dev/sdb doesn't contain a valid partition table". I had fstab auto mount sdb in the original server. I commented it out and for some reason I keep getting this error when using fdisk. Any ideas?

Hi,

When do you see the error message? What does fdisk -l display?

Regards
Ian Dobson

---

### Post by GriFF3n on 2011-08-17
> **ian dobson said:**
> Hi,

When do you see the error message? What does fdisk -l display?

Regards
Ian Dobson

```
Disk /dev/sdc: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/sdc doesn't contain a valid partition table
```

It looks like the disk is mounted, because I can write to it. But for some reason it does not contain the data it had on it originally.

---

### Post by ian dobson on 2011-08-17
> **GriFF3n said:**
> ```
Disk /dev/sdc: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/sdc doesn't contain a valid partition table
```

It looks like the disk is mounted, because I can write to it. But for some reason it does not contain the data it had on it originally.

any what does mount show. where do you think this drive is mounted?

Regards
Ian Dobson

---

