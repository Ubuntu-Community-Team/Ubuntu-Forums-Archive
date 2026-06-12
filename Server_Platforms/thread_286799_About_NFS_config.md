---
title: "About NFS config"
date: 2006-10-28
forum: Server Platforms
---

### Post by satimis on 2006-10-28
Hi folks,

Ubuntu-LAMP-server-amd64

I'm following the "server guide" to build the above server.

On NFS configuration (example);```

/ubuntu *(ro,sync,no_root_squash)
/home *(rw,sync,no_root_squash)
```

replaced * with ubuntu```

/ubuntu ubuntu(ro,sync,no_root_squash)
/home ubuntu(rw,sync,no_root_squash)
```

Ran;
$ sudo /etc/init.d/nfs-kernel-server start [Fail]

Also tried replacing * with localhost but still failed.

$ cat /et/hostname```

ubuntu

```

Please help.  TIA


B.R.
satimis

---

### Post by msimon1960 on 2006-12-03
Same problem -- the documentation doesn't define 'hostname format' and I've found no reference to this term anywhere.

Some examples in the documentation would be nice.

I'm finding tons on Windows<->Ubuntu but I'm trying to get a basic pure Ubuntu system working -- traditional file server and workstations all running Ubuntu.  You'd think it would be easier than this.

Matt.

---

### Post by wilso027 on 2006-12-03
You have to edit hosts.allow and hosts.deny.

hosts.deny
portmap: ALL : deny

hosts.allow
portmap: 192.168.0.100,192.168.0.101 : allow

You have to specify security in both places and then make sure you update any time you make changes to /etc/exports with:

sudo exportfs -r

Allan

---

