---
title: "SSDs Overheat in Zorin but not in Windows"
date: 2015-10-15
forum: Ubuntu/Debian BASED
---

### Post by Andreas_Georgiou on 2015-10-15
Hi,

I have a MSI GT72 laptop with 4 SSDs(Crucial_CT128M550SSD4, latest firmware) in RAID0.
I've installed Zorin OS(alongside Windows 10) which is based on Ubuntu 15.04. I noticed that my SSDs were running hotter in Zorin but not on Windows so I created a script to run on boot that sets "min_power" to link_power_management_policy to all hosts in /sys/class/scsi_host/. This helped a lot with the temperature and for 2-3 months SSDs were running smoothly at almost similar temps in Windows.(30C-45C). Suddenly, after 3 months, my computer started crashing and I found out that one of my SSDs is shutting down. I checked the temperature and I discovered that all of my SSDs were running extremely hot(90-100C) and that one of them occasionally shuts down because of the temps. The rest of the laptop runs really cool, even the HDD nearby runs on 35C.
I thought that one of my SSDs might me faulty causing all of them to run hot, but this does not happen in Windows at all.
Are there any solutions to this problem? If you need some kind of logs just ask.

```

$ uname -r
4.2.1-040201-generic

```

```

$ cat /etc/fstab
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
/dev/mapper/isw_dfbhhijcaj_Volume1p6 /                      ext4    noatime,discard,errors=remount-ro         0 1
/dev/mapper/isw_dfbhhijcaj_Volume1p5 /boot                  ext2    defaults,noatime,discard                  0 2
/dev/mapper/isw_dfbhhijcaj_Volume1p1 /boot/efi              vfat    defaults                                  0 1
/dev/mapper/isw_dfbhhijcaj_Volume1p7 /home                  ext4    defaults,noatime,discard                  0 2
UUID=B870A42770A3E9F8                /media/ageorgiou/DATA  ntfs-3g defaults,auto,uid=1000,gid=1000,umask=002 0 0
tmpfs                                /tmp                   tmpfs   defaults,noatime,mode=1777,size=15%       0 0

```

---

### Post by QIII on 2015-10-15
Moved to Ubuntu/Debian BASED

---

### Post by Andreas_Georgiou on 2015-10-15
Please mark this as SOLVED. I found out that a browser that I am using called vivaldi(which is not even at beta stage yet) seems to be causing the SSDs to overheat. I know it sound crazy but after exiting vivaldi, it does not exit properly and one process is still running in System Monitor. After force quitting that, the temperature drops really fast. I would imagine that something like this would cause the CPU temp to rise and not the SSD but for now I'll stick to Chrome

---

### Post by PaulW2U on 2015-10-15
> **Andreas_Georgiou said:**
> Please mark this as SOLVED.
Hi Andreas_Georgiou, as the originator of this thread you can do that.

At the top of the first post in the thread you'll see "Thread Tools". From the drop-down menu you'll see an option to mark the thread as being solved.

---

