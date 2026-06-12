---
title: "Help Server Error /dev/md0 at 100%"
date: 2010-08-25
forum: Server Platforms
---

### Post by svejkage on 2010-08-25
I have setup a software RAID5 server.  I setup an md0 RAID1 partition of size 1GB so that if any of the disks failed all the essential stuff should be duplicated across all disks and the server will still boot.  I also have a RAID5 /md1 partition of about 2TB.

I was attempting to install some packages with aptitude when it informed me I was out of device space.  I saw that indeed my /var/ directory was at 100%.  I noticed that most of the space was being taken up in /var/cache/apt/archives.  I ran apt-get clean, yet the output of df still indicates that /dev/md0 is full:

Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/md0                972056    972028         0 100% /
varrun                 1037220        84   1037136   1% /var/run
varlock                1037220         0   1037220   0% /var/lock
udev                   1037220        84   1037136   1% /dev
devshm                 1037220         0   1037220   0% /dev/shm
/dev/mapper/NIC-NIC_home
                     1932022952 618443480 1216211204  34% /home
/dev/mapper/NIC-NIC_tmp
                       1040280     34136    953716   4% /tmp
/dev/mapper/NIC-NIC_var
                       1040280    608716    379136  62% /var
  

Could someone help me clean up some of this space and figure out what's taking up all the room?

---

