---
title: "how tiny can Ubuntu Server be?"
date: 2018-01-11
forum: Server Platforms
---

### Post by cazz on 2018-01-11
If I look here a System Requirements
[https://help.ubuntu.com/community/Installation/SystemRequirements](https://help.ubuntu.com/community/Installation/SystemRequirements)
I can see the minimum of diskspace is 1,5 GB so if I gave it 10-20 GB then it is ok even when is time to run update of kernel and even maybe next version of Ubuntu server?

I ask this because I run some server in a virtualized server environment and some Ubuntu server is just going to do one thing and one thing only 

For example I going to have one ubuntu server with Samba and mdadm so I going to give the Ubuntu server access to three 3TB disk that I going to run RAID 0 and then make Samba share it to rest of my network.

---

### Post by LHammonds on 2018-01-12
You can easily install Ubuntu Server 16.04 LTS onto a 10GB  drive.   Here is a default install with Guided-LVM selected and OpenSSH  enabled:

```

root@ubuntu:/# vgdisplay
  --- Volume group ---
  VG Name               ubuntu-vg
  System ID
  Format                lvm2
  Metadata Areas        1
  Metadata Sequence No  3
  VG Access             read/write
  VG Status             resizable
  MAX LV                0
  Cur LV                2
  Open LV               2
  Max PV                0
  Cur PV                1
  Act PV                1
  VG Size               9.52 GiB
  PE Size               4.00 MiB
  Total PE              2437
  Alloc PE / Size       2431 / 9.50 GiB
  Free  PE / Size       6 / 24.00 MiB
  VG UUID               h53Zon-9HIb-6qgT-lgKQ-JOSV-T3px-jldSMa

```
```

root@ubuntu:/# df -h
Filesystem                   Size  Used Avail Use% Mounted on
udev                         477M     0  477M   0% /dev
tmpfs                        100M  3.2M   97M   4% /run
/dev/mapper/ubuntu--vg-root  8.3G  1.4G  6.5G  17% /
tmpfs                        497M     0  497M   0% /dev/shm
tmpfs                        5.0M     0  5.0M   0% /run/lock
tmpfs                        497M     0  497M   0% /sys/fs/cgroup
/dev/sda1                    472M   58M  391M  13% /boot
tmpfs                        100M     0  100M   0% /run/user/1000

```

The above is a clean install of 16.04.3.  The below is after doing the apt-get upgrade, dist-upgrade:

```
root@ubuntu:/# df -h
Filesystem                   Size  Used Avail Use% Mounted on
udev                         477M     0  477M   0% /dev
tmpfs                        100M  3.2M   97M   4% /run
/dev/mapper/ubuntu--vg-root  8.3G  1.8G  6.1G  22% /
tmpfs                        497M     0  497M   0% /dev/shm
tmpfs                        5.0M     0  5.0M   0% /run/lock
tmpfs                        497M     0  497M   0% /sys/fs/cgroup
/dev/sda1                    472M  106M  342M  24% /boot
tmpfs                        100M     0  100M   0% /run/user/1000
root@ubuntu:/# uname -a
Linux ubuntu 4.4.0-104-generic #127-Ubuntu SMP Mon Dec 11 12:16:42 UTC 2017 x86_64 x86_64 x86_64 GNU/Linux
```

**EDIT:** Since this is in a virtual environment, you can give it just what you need and add more disk space as needed later.  Very easy to expand if using LVM.  You can see the steps involved in the [Volume / Disk Management]("http://hammondslegacy.com/forum/viewtopic.php?f=40&t=220#p447") section of my install guide which explain how to add more drives and expand the volume group and file systems.  However, I wouldn't recommend choosing any of the partitioning options during install other than "Manual" and the same guide explains my reasons and how to do so.

LHammonds

---

### Post by Tadaen_Sylvermane on 2018-01-12
As an example I have my server set with a 10 gig root. Using just over half of it. I could shave another gig off that if I wasn't running Kodi. Thumbnails take up some space :/

---

