---
title: "USB stick detected but not visible &amp; created in /dev/"
date: 2010-12-28
forum: Server Platforms
---

### Post by veerudu on 2010-12-28
I am working on uBuntu 10.4 server. I am using kingston USB memory stick. When I plug in some times I don't get any messages on console.

#lsusb --> shows the list of USB devices. In which I find the Kingston memory stick. Means ..it is detected.

But when i type
#fdisk -l  I don't see any devices like /dev/sdc1

**NOTE:** Occasionally it works fine with /dec/sdc1 when ever I see messages on console as soon as I plug it in.

I even tired 
#sudo modprobe -r ehci_hcd
I got a FATAL: could not load /lib/modules/2.6.32-26-server/modules.dep: No such file or directory.

WHY IS IT WORKING OCCASIONALLY. WHY NOT MY USB STICK NOT GETTING DETECTED TO MOUNT ALWAYS?? 

Any help...

---

### Post by windependence on 2010-12-28
First try formatting the stick on another machine with FAT32.
 
If that doesn't work plug in the usb stick. Here is the command I would use assuming you have only one usb storage device.
 
```
 
sudo mkdir /mnt/usb_stick
sudo mount -t vfat /dev/sda1 /mnt/usb_stick

``` 
if that doesnt work then paste in the last 30 lines of running 'dmesg' for us to see.
 
-Tim

---

### Post by windependence on 2010-12-28
You can also try restarting famd. Remove the stick and try:
 
```
 
sudo /etc/init.d/fam restart

```
 
Then insert your stick again and see what happens.
 
-Tim

---

