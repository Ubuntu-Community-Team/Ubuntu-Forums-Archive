---
title: "Prevent disk spinup on nfs mount (exported mounts are softraids)"
date: 2012-12-30
forum: Server Platforms
---

### Post by oli_ on 2012-12-30
My homeserver is running a nfs server with some exports that are located on disks that spin down when there's no activity.
Whenever I boot my desktop those shares are auto-mounted via fstab. Every time they're mounted, those disks automatically spin up which I would like to prevent somehow (they should only spin up if I actually access data on them).

My setup looks like this:
/dev/sda - ssd running the system
/dev/sd[b-e] - harddisks that spin down. one small raid1 partition over all disks (mounted in /safehouse) and one large raid5 partition over all disks (mounted in /data), both are exported via nfs.

```
servers /etc/exports

/data		10.0.0.0/255.0.0.0(rw,sync,subtree_check,all_squash) # squash all access to nobody/nogroup
/safehouse	10.0.0.0/255.0.0.0(rw,sync,subtree_check,all_squash) # squash all access to nobody/nogroup

```

```
clients /etc/fstab

10.10.10.11:/safehouse		/media/safehouse	nfs	rw,nolock,bg	0 0
10.10.10.11:/data		/media/data		nfs	rw,nolock,bg	0 0
```

Is there any way to accomplish this? Any special mount options I overlooked maybe?

---

### Post by steeldriver on 2012-12-30
maybe you could mount them via autofs on the desktop instead of fstab?

---

### Post by oli_ on 2012-12-31
good idea, will remember that for the future.

I solved it now by modifying the clients fstab like this:
```
10.10.10.11:/safehouse	/media/safehouse	nfs	rw,nolock,bg,user,noauto	0 0
10.10.10.11:/data		/media/data		nfs	rw,nolock,bg,user,noauto	0 0

```

the client is running fedora 16; behaviour: shares are not mounted at boottime (noauto), but users are allowed to mount it (user). The share is listed in the filebrowser (nautilus) though and when you access it through the file browser its automatically mounted (but only then, accessing it on the shell does nothing!) which is good enough for me.

Will use the autofs setup in the future, thats much nicer.

---

