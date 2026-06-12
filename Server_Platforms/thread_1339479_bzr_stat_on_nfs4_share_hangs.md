---
title: "bzr stat on nfs4 share hangs"
date: 2009-11-27
forum: Server Platforms
---

### Post by abbec on 2009-11-27
I have a nfs4 share exported (/etc/exports further down) on a server running karmic. When i access bazaar branches on this share from my client machine and do bzr stat, everything just hangs.

/etc/exports line on the server
/srv/stuff 192.168.0.0/255.255.255.0(rw,sync,fsid=0,crossmnt,no_subtree_check)

I then mount the share with default options on a machine running karmic desktop edition (64-bit).

Similar behaviour has been discussed [here]("https://bugs.launchpad.net/ubuntu/+source/bzr/+bug/403697") but in that thread it's said that the problem goes away in karmic but that is not the case for me :(.

I can also add that the problem does not occur with other Bazaar commands like bzr diff or if i use NFS3.

Please help!

---

### Post by abbec on 2009-11-28
This message appears in syslog:

svc: failed to register lockdv1 RPC service (errno 97)

Can it be that bzr stat needs the nfs locking service maybe?

I have confirmed that this is the case. How do I make it running?

---

### Post by madrescher on 2009-11-30
I can that this issue.

~$ sudo mount -vvv  server:/home/export /mnt/nfs/
[sudo] password for xxx:
mount: fstab path: "/etc/fstab"
mount: mtab path:  "/etc/mtab"
mount: lock path:  "/etc/mtab~"
mount: temp path:  "/etc/mtab.tmp"
mount: UID:        0
mount: eUID:       0
mount: kein Typ angegeben – aufgrund des Doppelpunkts wird NFS angenommen
mount: spec:  "server:/home/export"
mount: node:  "/mnt/nfs/"
mount: types: "nfs"
mount: opts:  "(null)"
mount: external mount: argv[0] = "/sbin/mount.nfs"
mount: external mount: argv[1] = "shuttle:/home/server"
mount: external mount: argv[2] = "/mnt/nfs/"
mount: external mount: argv[3] = "-v"
mount: external mount: argv[4] = "-o"
mount: external mount: argv[5] = "rw"
mount.nfs: timeout set for Mon Nov 30 11:41:17 2009
mount.nfs: text-based options: 'addr=192.168.0.100'
mount.nfs: mount(2): Stale NFS file handle

kernel log repeated reports:
[13996.103654] svc: failed to register lockdv1 RPC service (errno 97).

lsb_release: Ubuntu 9.10

---

