---
title: "fstab"
date: 2013-08-22
forum: Virtualisation
---

### Post by ks46 on 2013-08-22
Whenever I login to my Virtual Machine (VMware 4.0.6. & the OS installed on it is Linux 12.04 Ubuntu & the OS of the host is Windows 7) I have the following message : 

An error occurred while mounting /proc/bus/usb

Here is my /etc/fstab : 


proc                                                                    /proc                 proc         nodev,noexec,nosuid              0           0
UUID=8c06d7b5-9f14-4e50-a9c7-33e74ece1635         /                       ext4         defaults                                1           2
UUID=f5a948747-97b7-4b4b-8a4a-711a35d0e1b5        none                 swap         sw                                      0           0
/dev/fd0                                                               /media/floppy0   auto          rw,user,noauto,exec,utf8        0           0
usbfs                                                                   /proc/bus/usb     usbfs        auto                                     0           0


Could you please tell me what is wrong with it?
Thank you

---

### Post by TheFu on 2013-08-26
What do the system logs say?

---

