---
title: "Ubuntu 10.10 randomly not mounting NFS shares - possible race condition?"
date: 2010-12-16
forum: Server Platforms
---

### Post by damang111 on 2010-12-16
NFS share is up.
it's set to r/w.  This is Ubuntu 10.10 NFS4 i believe.
exports file looks like this;
/data/feeder 10.10.10.1/255.255.255.0(rw,async,no_root_squash,no_subtree_check)

on the client,
/etc/fstab looks like this;
10.10.10.1:/data/feeder     /opt/feeder        nfs            rw          0 0

when I ls -la into /opt/feeder I see all the persmissions as:
4294967294:4294967294 instead of root:root

is there anything I'm doing wrong?
tia.

---

### Post by damang111 on 2010-12-16
NFS share is up.
it's set to r/w. This is Ubuntu 10.10 NFS4 i believe.
exports file looks like this;
/data/feeder 10.10.10.1/255.255.255.0(rw,async,no_root_squash,no_subtree_check)

on the client,
/etc/fstab looks like this;
10.10.10.1:/data/feeder /opt/feeder nfs rw 0 0

when I ls -la into /opt/feeder I see all the persmissions as:
4294967294:4294967294 instead of root:root

on the NFS server, ls -lan shows all uid's on the files as 0 .

Why is the NFS share/mount changing the uid's of the files?

is there anything I'm doing wrong?
tia.

---

### Post by amauk on 2010-12-16
idmapd is not running (either on the server, the client, or both)

idmapd maps account names to userIDs

in /etc/default/nfs-common on both client & server
add (or uncomment)```
NEED_IDMAPD=yes
```

---

### Post by damang111 on 2010-12-16
So it seems nfs-common is missing on all the recently Ubuntu 10.10 installations I made.
I ran apt-get install nfs-common , it installed fine but nfs-commmon is missing from /etc/init.d .
How do I restart nfs in that case?

tia.

---

### Post by cariboo on 2010-12-16
There is no file named nfs-common, it is only the package name, look for the following applications that are install by nfs-common:

[LIST]
[*]gssd
[*]idmapd
[*]rpc_pipefs
[*]statd
[/LIST]

---

### Post by damang111 on 2010-12-16
Thanks,
so how do I re-mount all fstab mounts?
I am trying to resolve a problem with multiple NFS mounts randomly not mounting after boot.

---

### Post by damang111 on 2010-12-16
no errors in /var/log/* in terms of NFS on the client or server side.
It seems 1 out of every 4 times I reboot the client host one of the NFS shares is not mounted properly (empty folder) and I need to do a 'mount -a' or reboot it again to get it back.  I don't want to do this.
here is my /etc/fstab file:

10.10.12.10:/data/uploads/      /opt/uploads        nfs         defaults          0 0
10.10.10.21:/opt/yum/repo/     /opt/repo       nfs            defaults          0 0

The first mount seems to be giving me problems after a bootup.  Not sure why. after mount -a it seems to be ok.  why is this?
It IS a different NIC on the server but I don't think that should matter.
there are no errors in the log.
Is there anything I can do to possible fix this?
the exports file looks like this on the problematic share;

/data/uploads 10.10.12.0/255.255.255.0(rw,async,no_root_squash,no_subtree_check)

any ideas?

---

### Post by damang111 on 2010-12-16
would adding the following to /etc/rc.local help?

sleep 5
mount -a 

?

---

### Post by cariboo on 2010-12-16
Seeing as all your threads are related to the same problem, I have consolidated them in one thread.

---

