---
title: "Ubuntu server 12.04 /dev/sdd1 disk full"
date: 2017-06-11
forum: Server Platforms
---

### Post by secoonder on 2017-06-11
Hello  
My /dev/sdd1 disk is full.i made the list
> 1)apt-get autoremove --purge
   apt-get autoclean
  apt-get clean
   rm -rf /var/cache/apt/archives/*
2)> uname -r
3.13.0-49-generic

> sudo apt-get remove linux-image-3.13.0-{43,44,45,46}-generic
 > ls /boot
-rw-r--r-- 1 root root  1164723 Mar 25  2015 abi-3.13.0-49-generic
-rw-r--r-- 1 root root   165782 Mar 25  2015 config-3.13.0-49-generic
drwxr-xr-x 3 root root     4096 Jan  1  1970 efi
drwxr-xr-x 3 root root     4096 Jun 11 16:45 grub
-rw-r--r-- 1 root root 20146285 May 15 20:51 initrd.img-3.13.0-49-generic
-rw-r--r-- 1 root root   176500 Mar 12  2014 memtest86+.bin
-rw-r--r-- 1 root root   178176 Mar 12  2014 memtest86+.elf
-rw-r--r-- 1 root root   178680 Mar 12  2014 memtest86+_multiboot.bin
-rw------- 1 root root  3525956 Mar 25  2015 System.map-3.13.0-49-generic
-rw------- 1 root root  5902944 Mar 25  2015 vmlinuz-3.13.0-49-generic
-rw------- 1 root root  5904856 Apr  9  2015 vmlinuz-3.13.0-49-generic.efi.signed 

But the problem is not solved

df -h output is 
> Filesystem      Size  Used Avail Use% Mounted on
udev            7.8G  4.0K  7.8G   1% /dev
tmpfs           1.6G  3.7M  1.6G   1% /run
/dev/sdd1       **454G  454G     0 100% /**
none            4.0K     0  4.0K   0% /sys/fs/cgroup
none            5.0M     0  5.0M   0% /run/lock
none            7.8G     0  7.8G   0% /run/shm
none            100M     0  100M   0% /run/user
/dev/sda1       2.0T  1.3T  606G  69% /_abc
/dev/sdb1       2.0T  1.6T  291G  85% /_def 

And 
> sudo du -sh /*
9.5M    /bin
41M     /boot
4.0K    /cdrom
1.6T    /_abc
4.0K    /dev
16M     /etc
1.8T    /_def


i think i have no choice to install a new computer a new disk.
Do you have another idea ?
Thank you very much for your help

---

### Post by Bashing-om on 2017-06-11
secoonder; Welp --- My 2 cents worth :

> 
1.6T /_abc
1.8T /_def

Obviously, files you added to the system and not under the control of the package management system.
Copy the data off of the directories that you can to another media - and remove them ... else
- As you say - add additional storage to the system.

[INDENT][INDENT]6 pounds of sugar in a 
[INDENT][INDENT][INDENT]5 pound sack
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by darkod on 2017-06-11
Aren't _abc and _def just mount points for sda1 and sdb1? In such case they shouldn't be taking space from sdd1.

I would suggest temporarily unmounting sda1 and sdb1 and then try again searching for folder sizes with:
```
sudo -i
cd /
du -sh *
```

That should show you more folders than you posted earlier. The reason why it is better to unmount sda1 and sdb1 first is that if at any moment you were copying data to /_abc and /_def and the disks were unmounted, the data would be saved in those folders in root (on sdd1). So, with sda1 and sdb1 unmounted the folders /_abc and /_def should ideally be empty.

---

