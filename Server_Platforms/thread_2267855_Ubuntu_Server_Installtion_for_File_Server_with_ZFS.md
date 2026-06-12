---
title: "Ubuntu Server Installtion for File Server with ZFS"
date: 2015-03-04
forum: Server Platforms
---

### Post by Andrew_La_Russa on 2015-03-04
Hi,

I want to setup file server with ZFS that I will use as a datastore for vmware ESXI. Would it be better to have a separate hard drive (or two to mirror) or using a USB stick to install. I think I can setup a raid mirror with USB sticks. Question is will there be a big performance hit booting off a USB drive? I originally thinking about picking up a couple small SSD drives, but the USB option would be a bit cheaper.

Thanks

---

### Post by darkod on 2015-03-05
For small installations like linux servers I prefer the option with CF-SATA adapter and using a CF memory card. You should be able to raid them easily. But that option is not as cheap as usb sticks. Also you could have issues with the HW playing nice with your MB. It has happened to me, although in general I still like the idea.

Also note that CF adapters would use up 1 or 2 SATA ports from the MB but not HDD caddies/space. You can use as many HDDs as the case supports, all for data/storage.

Booting of a usb stick should not have significant performance hit, plus you won't be rebooting the server that often, right? But some people don't like using them as OS disks. I think it mostly has to do with the fact that usb sticks are usually not designed for many read/write cycles.

---

### Post by MAFoElffen on 2015-03-07
I have 3 servers with onboard USB, just for that. USB 2.0 transfer rate is 60 MByte/s. USB 3.0 transfer rate is 640mbyte/s. CF Card transfer rate is 133 MByte/s.

But the OP confused me. He starting talking about using it as an install medium, then lost me when he went on to talk about using them for RAID, which would imply using them as the boot medium.

We have done it in the past with grub, but now-- Me and another associate are playing with setting up Easyboot on 2.5 inch drives, with many Windows, OSX and Linux ISO files, setup as both EFI and legacy MBR... as our install medians, using USB 3.0 adapters. Both of us volunteer for a computer recycler, so have to install what the hardware will support, orders, etc. So then we each will have one drive to install all OS'es we support.

---

