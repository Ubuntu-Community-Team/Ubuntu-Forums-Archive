---
title: "ZFS - removing cache drive"
date: 2017-02-03
forum: Server Platforms
---

### Post by thumper332 on 2017-02-03
First off, how I have things set up....
miI originally set up this box intending to run FreeNAS.  After setting that up with USB drives for boot, I installed two 6TB drives mirrored with an SSD as a cache.  I wanted to try Ubuntu instead, so I used those three drives to do so.  I formatted the SSD to use as the OS drive, installed ubuntu, and imported the two zfs drives with the data still on them.  Everything works great, and I'm happy, however, the pool is still expecting the cache drive to be there, so the pool is degraded, and won't let me scrub.  One of my 6TB drives (both new) has more vibration than it should and I'm going to send it back in for a swap.  I thought I would just scrub, power down and remove the drive, boot back up and make sure everything is there, and cross my fingers while I wait for the drive replacement.  Once the new drive comes in I would resilver and everything should be fine.  However, it won't let me scrub (or doesn't appear to) in a degraded state, and I don't want to send the drive in until I scrub.  Hoping that makes sense so far.  

First off, am I correct that since I'm mainly running this box as a media server (Plex, Couchpotato, Deluge), I won't see much benefit from using an ssd cache.  I used it with my FreeNAS install because I had it, so might as well use it (256Gb Samsung 850 EVO).  They're really cheap, so if someone thinks I should just buy another one and like the results I will.  However, how can I tell ZFS to stop expecting it for now?

Here is what I've tried:

sudo zpool status
  
returns:  

```
pool: Tank
state: ONLINE
status: One or more devices could not be used because the label is missing or
        invalid.  Sufficient replicas exist for the pool to continue
        functioning in a degraded state.
action: Replace the device using 'zpool replace'.
   see: [http://zfsonlinux.org/msg/ZFS-8000-4J](http://zfsonlinux.org/msg/ZFS-8000-4J)
  scan: scrub repaired 0 in 0h0m with 0 errors on Tue Jan 31 23:28:55 2017
config:

        NAME                                    STATE     READ WRITE CKSUM
        Tank                                    ONLINE       0     0     0
          mirror-0                              ONLINE       0     0     0
            sdb2                                ONLINE       0     0     0
            sdc2                                ONLINE       0     0     0
        cache
          71e7694f-e061-11e6-bd1f-3497f600ddaf  UNAVAIL      0     0     0

errors: No known data errors
```



so I run ...

```
sudo zpool remove Tank 71e7694f-e061-11e6-bd1f-3497f600ddaf
```


returns:  cannot remove 71e7694f-e061-11e6-bd1f-3497f600ddaf: no such device in pool



and tried :

```
sudo zpool remove cache 71e7694f-e061-11e6-bd1f-3497f600ddaf
```

returns:  cannot open 'cache': no such pool

---

### Post by thumper332 on 2017-02-08
still have this issue

---

### Post by deadflowr on 2017-02-09
*Thread moved to **Server Platforms**.*

---

### Post by darkod on 2017-02-09
Can something like this help?
[http://unix.stackexchange.com/questions/130846/how-to-remove-broken-zil-disk-from-zfs-pool](http://unix.stackexchange.com/questions/130846/how-to-remove-broken-zil-disk-from-zfs-pool)

NOTE: I haven't tried this solution and do not know how it will affect your data, I just used google search...

It's too late to say it now, but if you planned to do this you should have removed the cache device in FreeNAS before installing another OS. In such case the pool import should have been OK in theory.

---

### Post by Thurloat on 2017-04-04
-- nvm, misread your post --

Your answer might lie here: [https://github.com/zfsonlinux/zfs/issues/1530](https://github.com/zfsonlinux/zfs/issues/1530), perhaps you need to refer to the GUID (you should be able to get it via "zpool status -g")

Further digging has uncovered this post: [http://sysadm.mielnet.pl/zfs-zpool-remove-phantom-disk/](http://sysadm.mielnet.pl/zfs-zpool-remove-phantom-disk/) where you use `zdb` to get the disk ID you'd like to remove.

---

