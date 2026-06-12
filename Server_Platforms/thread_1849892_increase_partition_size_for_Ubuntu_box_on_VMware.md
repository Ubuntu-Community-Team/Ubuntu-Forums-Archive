---
title: "increase partition size for Ubuntu box on VMware"
date: 2011-09-25
forum: Server Platforms
---

### Post by hphan082 on 2011-09-25
Hi everyone, I'm completely extremely new to Ubuntu, Linux in general. I don't even understand most of the term in here.
I just inherite a Ubuntu/Centreon VM from our previous Network admin. We have been running into performance issue with Centreon, and I came to a conclusion that it might be because there are no more disk space in the VM. 
After googling for a past week, I was able to install gparted. Change root and administrator account password. (i'm a windows guys:confused:).
After I run df -h, I got the below info
File System     Size   Used   Avail   Use%    Mounted on
/dev/sda1        39G    37G       0   100%     /
varrun          506M   136K    506M     1%     /var/run
varlock         506M      0    506M     1%     /var/lock
udev            506M    40K    506M     1%     /dev/
devshm          506M    24K    506M     1%     /dev/shm
lrm             506M    40M    467M     8%     /lib/modules/2.6.24-24-generic/volatile
gvfs-fuse-daemon 39G    37G       0   100%     /home/administrator/.gvfs

When I tried to run Vmware tools installation, I got an error said no more disk space. Also, during the time I'm typing this thread, I tried to log off and relogon as another user within Ubunto to see if I got a different df message, I got a notification said that something cannot write into something because not enough disk space, therefore I can't login.
I have given the machine more disk space through virtual center, but I don't know how to actually go into the Ubuntu box and increase the disk/partition. 
Can you guys help me? I want to know if my disk is actually running out of space? and if it does, what should I do to increase it. When I run Gparted, i only see ext3 (/dev/sda1) (38.32GB), extended (dev/sda2) = 1.68GB, linux-swap (dev/sda5 ) = 1.68GB, and unallocatted (20GB)
PLease help me! I'm so lost. 

Oh, and if I post this in the wrong forum, please excuse me. I don't know where to look for the version of Ubuntu. I'm running centreon on it, where it send email notification to us for nagios/centreon alert, so I'm assuming this is a server version.

---

