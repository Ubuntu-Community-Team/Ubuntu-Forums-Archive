---
title: "zpool import hanging on Ubuntu 19.04"
date: 2019-08-28
forum: Server Platforms
---

### Post by Silicon Knight on 2019-08-28
Hi there, I've looked everywhere to solve this but can't seem to find an answer anywhere for my version:
```
$ sudo modinfo zfs | grep version version:        0.7.12-1ubuntu5
srcversion:     DF2FAADF923F083105D0538

```

and running
```
$ hostnamectl   Static hostname: storage
         Icon name: computer-server
           Chassis: server
  Operating System: Ubuntu 19.04
            Kernel: Linux 5.0.0-25-generic
      Architecture: x86-64
```

When I perform:
```
$ sudo zpool import pool2
```
the process just hangs endlessly.  I've tried to wait for days and nothing happens.  I do however get:
```
PANIC at space_map.c:115:space_map_load()
``` in my log file and the only way to get zpool command to work again is to reboot.  The PID keeps running even if I try to kill it.

I do have two zpools (zpool1 / zpool2) and zpool1 is fine and running w/o issue however zpool2 is definitely a problem.  

There is one other thing I have noticed and clearly I screwed up somehow, my hdd SDC seems to be shared between zpool1 and zpool2 as you can see here:
```
$ sudo zpool import
  pool: pool2     id: 681544990157547671
  state: ONLINE
 status: Some supported features are not enabled on the pool.
 action: The pool can be imported using its name or numeric identifier, though
    some features will not be available without an explicit 'zpool upgrade'.
 config:


    pool2       ONLINE
      raidz1-0  ONLINE
        sdf     ONLINE
        sdg     ONLINE
        sdi     ONLINE
        sdh     ONLINE
    spares
      sdc
$ sudo zpool status -v
  pool: pool1
 state: ONLINE
  scan: resilvered 80K in 0h0m with 0 errors on Wed Aug 28 13:28:00 2019
config:


    NAME        STATE     READ WRITE CKSUM
    pool1       ONLINE       0     0     0
      raidz1-0  ONLINE       0     0     0
        sdb     ONLINE       0     0     0
        sdd     ONLINE       0     0     0
        sda     ONLINE       0     0     0
        sdc     ONLINE       0     0     0


errors: No known data errors


```

So it looks to me that both pools are healthy and should be able to be imported. If I check the SMART monitor for all my drives they are functioning as normal and none are in failure or prefail.

I'm at a loss for what to do, the pools were working fine even with the shared SDC drive, I suppose since its a spare its not actually active so it wasn't historically causing an issue (not sure how I did that).  I can't seem to detach the spare since I can't get the zpool imported.  I did try 
```
$ zpool import -f pool2
```
and it fails also and simply hangs.

I had previously been running 18.04LTS and thought I'd start fresh so I put 19.04 in and the same issue is happening.

Any ideas?

---

### Post by darkod on 2019-08-29
Unfortunately I can't help you much because I have no in depth ZFS knowledge.

But if you tried 19.04 and the problem is still there, I would go back to 18.04 LTS and try to troubleshoot it. It might not be correct towards the ubuntu developers saying this, but I consider all standard version between two LTS versions as "lab rats". I wouldn't use them on any production server, even home server.

There are special cases where you need to test if something is included in the new version but that is usually only for short term lab tests. Unless you are sure 19.04 offers you something more, I would go back to the LTS.

Now another thing: Have you tried removing sdc from pool1 and after that also removing it as spare from pool2? Not sure if you can remove it from pool2 before you can import it. This is maybe something to try to make sure it is not affecting your import command.

---

### Post by Silicon Knight on 2019-08-29
Thanks for the reply, I did try taking SDC out of the pool both by off lining the drive and by removing it and leaving it in a degraded state however it still hangs with the same error.  

I had read (in previous versions) that it was an issue with zfs which was fixed so I moved to 19.04 to try a newer version.  No dice.

---

### Post by darkod on 2019-08-29
If you think you are affected by a bug that has been patched, did you compare the zfs version in 18.04, the one in 19.04 and the latest zfs directly from their team?

Maybe they offer a deb file to install on ubuntu, or instructions how to compile the latest version if that has the bug patched? In such case don't use the version in the ubuntu repo, try the zfs team repo (if any) or compiling.

I assume you use the package included with ubuntu, otherwise if you are compiling yourself, it wouldn't matter much which version of ubuntu you are using.

When you say you tried removing sdc, how about removing it from the spare list of pool2? Is that possible at all with pool2 not being imported right now? Because it is still listed in pool2 so you obviously didn't remove it as spare member.

---

