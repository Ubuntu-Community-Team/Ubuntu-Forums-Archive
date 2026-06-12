---
title: "/dev/mapper/ubuntu--vg-root filling up"
date: 2017-11-05
forum: Server Platforms
---

### Post by david_brown on 2017-11-05
Hi,

I notice this is getting larger on a daily basis by a couple of percent. The output of df -h is below. The operating system is on a separate ssd drive. I use it as a home media server it was normally about 4% of the drive and suddenly started growing. I've looked at loads of information in this forum before posting but am frankly stumped and would appreciate some help please.

I've checked for old kernels, regularly run clean, autoclean and autoremove. It's Ubuntu 16.04 I'm running

Thanks


Filesystem                   Size  Used Avail Use% Mounted on
udev                         1.7G     0  1.7G   0% /dev
tmpfs                        345M   36M  309M  11% /run
/dev/mapper/ubuntu--vg-root  216G  101G  105G  49% /
tmpfs                        1.7G   12K  1.7G   1% /dev/shm
tmpfs                        5.0M     0  5.0M   0% /run/lock
tmpfs                        1.7G     0  1.7G   0% /sys/fs/cgroup
/dev/sda1                    1.8T  1.6T  252G  87% /media/backuphdd
/dev/sdb1                    2.7T  1.9T  850G  70% /media/mainhdd
/dev/sdd1                    437G  371G   43G  90% /media/alicearchive
/dev/sde1                    1.8T  330G  1.5T  18% /media/archiveusb
/dev/sdc1                    472M   58M  390M  13% /boot
tmpfs                        345M     0  345M   0% /run/user/1000

---

### Post by darkod on 2017-11-05
You can become root, go to / and check size of the folders. After that go into one of the big folders and run the same command. It will show which folder has what size. But it only goes one level down, so you have to follow it going into the folder where you are interested to run it.

```
sudo -i
cd /
du -sh *
```

---

### Post by david_brown on 2017-11-05
Hi,

this is the output:-

root@ubuntu:/# du -sh *
16M     bin
56M     boot
12K     dev
8.3M    etc
83M     home
0       initrd.img
455M    lib
4.0K    lib64
16K     lost+found
4.1T    media
4.0K    mnt
174M    opt
du: cannot access 'proc/20919/task/20919/fd/4': No such file or directory
du: cannot access 'proc/20919/task/20919/fdinfo/4': No such file or directory
du: cannot access 'proc/20919/fd/4': No such file or directory
du: cannot access 'proc/20919/fdinfo/4': No such file or directory
0       proc
20K     root
36M     run
13M     sbin
4.0K    snap
4.0K    srv
0       sys
4.0K    tmp
1.2G    usr
99G     var
0       vmlinuz

---

### Post by darkod on 2017-11-05
There you go, 99GB in /var. Now go into /var with 'cd /var' and run the same du command. And keep doing that until you find the file/folder...

---

### Post by david_brown on 2017-11-05
Seems like the big folder is Var, and drilling down /var/lib has 99G and drilling down again shows /var/lib/plexmediaserver is the 99G

I guess Plex forums is my next call!

Thanks

---

### Post by ajgreeny on 2017-11-05
That really is a huge plexmediaserver folder; on my system where I run Plex that folder is 1.6GB, and I thought that was large.

Do you have a huge number of media file which are served by Plex; I have about 500GB of music, videos and photos.

---

