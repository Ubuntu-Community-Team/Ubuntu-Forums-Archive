---
title: "Tevion high-speed dvd maker"
date: 2008-08-29
forum: Ubuntu Studio
---

### Post by iarspider on 2008-08-29
Hi, all!

Last year I've purchased the "Tevion high-speed DVD maker" from Aldi. I use it to convert videos made with a Sharp 8mm camera. The device came with windows-only software, and as I am moving to linux (ubuntu) now I need to figure out how to make it work.

The device is identified as 
```

Bus 007 Device 005: ID eb1a:2860 eMPIA Technology, Inc.

```

By Googling I discovered that the appropriate module is em28xx. 
But the devide didn't connect after modprobe:

```

[  438.408460] em28xx v4l2 driver version 0.0.1 loaded
[  438.408535] usbcore: registered new interface driver em28xx
[  442.405219] usb 7-3: new high speed USB device using ehci_hcd and address 5
[  442.477619] usb 7-3: configuration #1 chosen from 1 choice

```

Googling some more gave me a link to [Ubuntu Wiki](https://wiki.ubuntu.com/em28xx), which described a procedure to install another version of em28xx, but that didn't help either.

The only other useful information about using the device under linux is [here](http://www.mcentral.de/wiki/index.php5/Em2880_FAQ3#Hangs_when_snapping_frame_KWorld_USB2800.3F.3F). 

Any ideas on what to do next?

---

### Post by iarspider on 2008-08-31
I've decided to repeat installation of new em28xx module, and suddenly notices that the module was being build for kernel 2.6.24-19, whilst I'm using 2.6.24-21. After removing all the packages for old kernel and redownloading/rebuilding em28xx the device got recognized (at last!). 

Alas, my joy was short: it seems that this version of em28xx breaks uvcvideo:
```

$ modprobe uvcvideo
FATAL: Error inserting uvcvideo (/lib/modules/2.6.24-21-generic/updates/uvcvideo.ko): Unknown symbol in module, or unknown parameter (see dmesg)
$dmesg[  185.808260] uvcvideo: disagrees about version of symbol video_devdata
[  185.808264] uvcvideo: Unknown symbol video_devdata
[  185.808545] uvcvideo: disagrees about version of symbol video_unregister_device
[  185.808546] uvcvideo: Unknown symbol video_unregister_device
[  185.808634] uvcvideo: disagrees about version of symbol video_device_alloc
[  185.808635] uvcvideo: Unknown symbol video_device_alloc
[  185.808696] uvcvideo: disagrees about version of symbol video_register_device
[  185.808697] uvcvideo: Unknown symbol video_register_device
[  185.808886] uvcvideo: disagrees about version of symbol video_device_release
[  185.808887] uvcvideo: Unknown symbol video_device_release

```

Currently searching for a solution.

---

### Post by iarspider on 2008-09-12
Ok, took the move and upgraded to alpha version of Ubintu 8.10. The device is now recognized, but as a "PointNix Intra-Oral Camera". Will try and find the correct device# for it.

---

