---
title: "ZFS Pool reporting wrong size"
date: 2011-11-09
forum: Server Platforms
---

### Post by jm.mico on 2011-11-09
Hello world;

I am in the process of building a home server with an old laptop and 3x500GB External USB HDD (RAID Z1)


I am having a problem regarding the reported size, as I understand it, I should be having something in the 1TB. However zfs list reports 291GB '!??

Do you have a clue why this is happening? I created the pool with the following command:
sudo zpool create -f -o ashift=12 datasafe raidz /dev/sdd /dev/sde /dev/sdf

The ashift=12 aligns the blocks to 4K (I am unsure if this was required, but in my oder laptop the speeds I was getting were in the order of 40kilobytes/s, and I though it could be something with being 4K HDD)

```
root@dell-server:~# zfs list
NAME       USED  AVAIL  REFER  MOUNTPOINT
datasafe   291G      0   291G  /datasafe
```

```
root@dell-server:~# zpool list datasafe
NAME       SIZE  ALLOC   FREE    CAP  DEDUP  HEALTH  ALTROOT
datasafe   444G   437G  6.94G    98%  1.00x  ONLINE  -
```

I just plain don't get it. Where is the 1TB that I should be having??

1000xTHnks :)

---

