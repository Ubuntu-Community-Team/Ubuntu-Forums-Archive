---
title: "Raw Disk Virtualization"
date: 2011-04-17
forum: Virtualisation
---

### Post by hiKen on 2011-04-17
Hi

I've been trying to find a way to virtualize my windows 7 installation in ubuntu 10.10, so that I can avoid having to reboot every time I have to use windows aplications.

I saw some tutorials on how to do this, but they seem outdated, and it seems to be a quite delicate operation and I don't want to mess anything up, so I'd like to check if anyone has tried sucessfully this type of virtualization.



CUmpz

---

### Post by joberly on 2011-04-19
You can use [Disk2vhd]("http://technet.microsoft.com/en-us/sysinternals/ee656415.aspx") to build the image. What virtualization solution are you using? VirtualBox supports .VHD disks, fyi.

Seems pretty straightforward, run the Disk2vhd and create the disk. Then in VirtualBox (for example) create a new machine, and select 'Use Existing Hard Disk' under the Virtual Hard Disk step in the process. Navigate to where that .vhd is located, and that should be about it.

---

