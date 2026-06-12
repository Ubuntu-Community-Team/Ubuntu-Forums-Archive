---
title: "Hangs on reboot: must hold power button then press again"
date: 2013-08-21
forum: Server Platforms
---

### Post by MFI-Spencer on 2013-08-21
I am using an older HP Desktop model as a server trying to run a database app. When I reboot the machine using ```
sudo reboot
```

The hardware gets stuck and will never actually shut all the way down.

If I run ```
sudo poweroff
```
The hardware will turn off.

I had this problem before with Ubuntu Desktop edition 10.04 and just to be sure the hardware was not bad I installed windows again reboot, shutdown, hibernate, and sleep all functioned as expected. Now I have installed Ubuntu server 12.04.2 64bit and I have only tried the reboot and poweroff as noted above. 



Hardware information using 

```
sudo dmidecode -t 2
```
```
SMBIOS 2.3 present.

Handle 0x0002, DMI type 2, 8 bytes
Base Board Information
   Manufacturer: ASUSTeK Computers INC.
   Product Name: Diablo
   Version: 1.xx
   Serial Number: x312345678
```

---

### Post by chrisguk on 2013-08-23
In this case you would be better off using the following commands:


This reboots the machine and closes all processes
```
sudo shutdown -r now
```

This shuts the machine down and halts (no reboot)
```
sudo shutdown -h now
```

---

### Post by nerdtron on 2013-08-24
Maybe you have mounted some network shares that stops the computer from rebooting. I have this problem when I mounted an RBD disk from a ceph cluster to Ubuntu.

---

