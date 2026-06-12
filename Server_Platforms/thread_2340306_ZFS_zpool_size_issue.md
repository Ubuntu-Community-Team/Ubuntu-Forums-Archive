---
title: "ZFS zpool size issue"
date: 2016-10-17
forum: Server Platforms
---

### Post by alxhoff-d on 2016-10-17
Hi,


I am hoping to get some advice as I am a little confused from what I have found online and given the sensitive nature of my datastore I don't want to randomly try commands.


My set up is Ubuntu server 14.04 LTE 4.2.0-42 running the ubuntu-zfs package. My problem is that I have a zpool made up of two vdevs. Vdev 1 is 4 x 2TB drives running in RAID-Z1 and the second vdev is 3 x 3TB drives also running in RAID-Z1. This should give me a usable space of around 12TB. 

When I run 

```
 sudo zpool list 
```

I get the following

```
 alxhoff@FlyingNimbus:~$ sudo zpool list
NAME        SIZE  ALLOC   FREE  EXPANDSZ   FRAG    CAP  DEDUP  HEALTH  ALTROOT
datastore  13,2T  9,13T  4,08T         -    25%    69%  1.00x  ONLINE  -

```

I am unsure of how to expand my datastore (called datastore) to take up the full available size of the zpool instead of the 9.13TB that it is currently using.

Thank you

---

### Post by darkod on 2016-10-17
Do you have any zfs datasets inside the pool? If you do, they might be limited in size and thus not using any available free space. I had some notes about checking this on zfs but I'll have to get home to find them.

PS. Try something like:
```
sudo zfs list
```
and
```
sudo zfs get quota <dataset>
```

That should give you some more info.

---

