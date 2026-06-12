---
title: "Ubuntu 22.04 kernel update 6.5-&gt;6.8: no boot, initramfs, busybox"
date: 2024-10-16
forum: Ubuntu/Debian BASED
---

### Post by alfredino on 2024-10-16
Hi,


I have a system with zentyal 8 based on ubuntu 22.04.5 LTS. The system works well with kernel 6.5.0-41-generic while if I install the latest hwe kernel 6.8.0-47-generic it fails to boot with the following error:


```
     Volume group "vgserver" not found
     Cannot process volume group vgserver 
    Gave up waiting for suspend/resume device
     Volume group "vgserver" not found
     Cannot process volume group vgserver 
    Gave up waiting for root file system device. Common causes:
    -Boot args (cat /proc/cmdline)
      -Check rootdelay= (did the system wait long enough?)
    -Missing modules (cat /proc/modules; ls /dev) 
    ALERT! /dev/mapper/vgserver-root does not exist. Dropping to a shell! 
    
    Busybox v1.30.1 (ubuntu 1:1.30.1-7ubuntu3.1 built in shell (ash))
    (initramfs)

```

After installing the latest kernel I tried to run: update-initramfs -u -k. However, it have not solved the problem.


What can I do? Is there any way to have the latest kernel?


Thank you

---

### Post by howefield on 2024-10-16
Thread moved to the "*Ubuntu/Debian BASED*" forum.

---

