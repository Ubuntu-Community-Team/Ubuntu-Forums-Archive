---
title: "Cannot boot after 9.10 upgrade on vps (cause cannot change kernel at boot)"
date: 2009-12-06
forum: Server Platforms
---

### Post by alex88 on 2009-12-06
Hi all, i've a VPS with installed ubuntu 9.04 on xen virtualization, the kernel version is 2.6.18-128.7.1.el5xen and also installing new kernel with apt-get i'm unable to change it on boot. My vps has hypervm control panel, and there is no way to manage boot (just a "append to inittab" link), also my /boot folder is empty.
The problem is upgrading on 9.10, cause the old kernel gives lots of errors:

```
[    0.135786] rtc: IRQ 8 is not free.                                          
[    0.137269] i8042.c: No controller found.                                    
Loading, please wait...                                                         
Couldnt get a file descriptor referring to the console                          
FATAL: Error inserting fan (/lib/modules/2.6.24-23-xen/kernel/drivers/acpi/fan.k
o): No such device                                                              
FATAL: Error inserting thermal (/lib/modules/2.6.24-23-xen/kernel/drivers/acpi/t
hermal.ko): No such device                                                      
mountall:/proc: unable to mount: Device or resource busy                        
mountall:/proc/self/mountinfo: No such file or directory                        
mountall: root filesystem isn't mounted                                         
init: mountall main process (1670) terminated with status 1                     
General error mounting filesystems.                                             
A maintenance shell will now be started.                                        
CONTROL-D will terminate this shell and re-try.                                 
Give root password for maintenance                                              
(or type Control-D to continue):
```so i mean, how can i check how this crap boots? or, removing the older kernel and installing a new one will update boot??


As i said:

/boot is empty

/etc/fstab
```
/dev/sda1 /                       ext3    defaults,usrquota,grpquota,relatime        1 1
none                    /dev/pts                devpts  gid=5,mode=620  0 0
none                    /dev/shm                tmpfs   defaults        0 0
none                    /proc                   proc    defaults        0 0
none                    /sys                    sysfs   defaults        0 0
/dev/sda2 swap                    swap    defaults        0 0
```

---

