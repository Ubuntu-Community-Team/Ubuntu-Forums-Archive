---
title: "Share zfs-dataset via nfs stopped working"
date: 2019-03-24
forum: Server Platforms
---

### Post by mattiash on 2019-03-24
I rebuilt my server last week, setup a zfs pool, shared a few datasets, today I had to reboot a server that was connected to the storage server via NFS and after this it cant mount the NFS shares from the storage server. 
This is the error I get:
mount.nfs: requested NFS version or transport protocol is not supported

First I thought hey it is the wrong NFS version, so I tried -t nfs4 then I get access denied...

And on the storage server is see this when I take a service status on the NFS-server:
exportfs: Failed to stat /zfspool/media: No such file or directory

I have zfs set sharenfs for this dataset.

So here's my exports file:
/zfspool/media      10.20.1.0/24(rw,sync,no_subtree_check)

What am I doing wrong?
Atm, I feel like I am all over the place... please help!

---

### Post by houstonbofh on 2019-03-27
Did you run updates?  How are you mounting nfs?

---

