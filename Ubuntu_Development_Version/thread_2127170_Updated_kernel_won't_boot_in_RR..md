---
title: "Updated kernel won't boot in RR."
date: 2013-03-17
forum: Ubuntu Development Version
---

### Post by mdalacu on 2013-03-17
Same updates, but for me is still does not boot with 3.8 kernel, stuck in busybox. Also the livecd is no help for me, same result.
The 3.8 kernel does not see any of my disks, only the CDROM drive. I have AMD 890FX chipset. 
If, from grub i chose old Oneric kernel 3.5.0.26 all is working fine in Raring.

What can i do?
Thank you.

---

### Post by zika on 2013-03-17
> **mdalacu said:**
> Same updates, but for me is still does not boot with 3.8 kernel, stuck in busybox. Also the livecd is no help for me, same result.
The 3.8 kernel does not see any of my disks, only the CDROM drive. I have AMD 890FX chipset. 
If, from grub i chose old Oneric kernel 3.5.0.26 all is working fine in Raring.

What can i do?
Thank you.Did You re-create initramfs images for all kernels?
```
sudo update-initramfs -ck all
```
or at least for kernel You want to try?
Usually only newest kernel get itsinitramfs image recreated automatically...

---

### Post by mdalacu on 2013-03-18
> **zika said:**
> Did You re-create initramfs images for all kernels?
```
sudo update-initramfs -ck all
```
or at least for kernel You want to try?
Usually only newest kernel get itsinitramfs image recreated automatically...

The initramfs image file size is correct and i already  had 2 kernel updates 3.8.0.12 and 3.8.0.13. I have also rebuild it with the same file size and result. Alos the live CD , if i choose Try Ubuntu does not work, same result. If i wait a little longer and type exit in busybox, same result.
I think that is something wrong with 3.8 kernel that none of my sata hdd does not get listed in /dev, only the CD ROM. I reiterate that using 3.5 kernel i have no problems in Raring.
I have attached the output from lshw. 
What else can i do? How can i investigate that indeed it is a problem with 3.8 kernel or something is wrong with my setup?
Thank you very much.

---

### Post by Harry33 on 2013-03-19
Sorry to interrupt, but this discussion (original thread) is not about kernel issues.
This was supposed to be a thread concerning issues with new udev and libudev (from systemd) and the compatibility of initramfs-tools to such new environment.
As this issue is completely solved now, it would be a better idea to open up a new thread regarding other issues.

---

### Post by zika on 2013-03-19
> **Harry33 said:**
> Sorry to interrupt, but this discussion (original thread) is not about kernel issues.
This was supposed to be a thread concerning issues with new udev and libudev (from systemd) and the compatibility of initramfs-tools to such new environment.
As this issue is completely solved now, it would be a better idea to open up a new thread regarding other issues.You're right. The only reason that I enterd this talk was to help to create new kernel images... Just because there is sort of problem with that because upgrade process do update-initramfs on newest kernel not on the one that is currently being used... It might create confusion sometimes... I've resolved that with myself years ago but confusion is still present with other users... That is the point that I considered on-topic in this thread abd reason I wrote my posts here...

---

### Post by CharlesA on 2013-03-19
Moved to own thread.

---

