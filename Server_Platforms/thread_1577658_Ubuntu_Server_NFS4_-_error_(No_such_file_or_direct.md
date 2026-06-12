---
title: "Ubuntu Server NFS4 - error (No such file or directory)"
date: 2010-09-19
forum: Server Platforms
---

### Post by nicolasdiogo on 2010-09-19
Hi folks,

i have problem in setting up a NFS4 server to share some locations.

i followed this document - section around non-secure connections:
[https://help.ubuntu.com/community/SettingUpNFSHowTo](https://help.ubuntu.com/community/SettingUpNFSHowTo)

and my /etc/default/nfs-kernel-server now looks like this.
```

# Number of servers to start up
RPCNFSDCOUNT=4

# Runtime priority of server (see nice(1))
RPCNFSDPRIORITY=0

# Options for rpc.mountd.
# If you have a port-based firewall, you might want to set up
# a fixed port here using the --port option. For more information, 
# see rpc.mountd(8) or http://wiki.debian.org/?SecuringNFS
RPCMOUNTDOPTS=

# Do you want to start the svcgssd daemon? It is only required for Kerberos
# exports. Valid alternatives are "yes" and "no"; the default is "no".
#	NEED_SVCGSSD=
NEED_SVCGSSD=no # no is default

# Options for rpc.svcgssd.
RPCSVCGSSDOPTS=

```

as per instruction my /etc/default/nfs-common :
```

# If you do not set values for the NEED_ options, they will be attempted
# autodetected; this should be sufficient for most people. Valid alternatives
# for the NEED_ options are "yes" and "no".

# Do you want to start the statd daemon? It is not needed for NFSv4.
NEED_STATD=

# Options for rpc.statd.
#   Should rpc.statd listen on a specific port? This is especially useful
#   when you have a port-based firewall. To use a fixed port, set this
#   this variable to a statd argument like: "--port 4000 --outgoing-port 4001".
#   For more information, see rpc.statd(8) or http://wiki.debian.org/?SecuringNFS
STATDOPTS=

# Do you want to start the idmapd daemon? It is only needed for NFSv4.
#    NEED_IDMAPD=
NEED_IDMAPD=yes

# Do you want to start the gssd daemon? It is required for Kerberos mounts.
#    NEED_GSSD=
NEED_GSSD=no # no is default

```

after restarting the NFS4 server
```

/etc/init.d/nfs-kernel-server restart

```

my /etc/exports :

```

/opt/nfs_exports 192.168.1.0/24(ro,sync,insecure,root_squash,no_subtree_check,fsid=0,anonuid=65534,anongid=65534)

/opt/nfs_exports/VM01 192.168.1.0/24(rw,nohide,sync,insecure,root_squash,no_subtree_check,anonuid=65534,anongid=65534)
/opt/nfs_exports/ISO01 192.168.1.0/24(rw,nohide,sync,insecure,root_squash,no_subtree_check,anonuid=65534,anongid=65534)

```

since my server has two IP:
192.168.1.251
192.168.1.254

i believe the IP range specified on the /etc/exports above will be correct.


however, when i try mounting any of these share i get an error message, please note that i am trying to mount it on the localhost using its IP:
```

mount -t nfs4 192.168.1.254:/opt/nfs_exports/ISO01 mnt/
mount.nfs4: mounting 192.168.1.254:/opt/nfs_exports/ISO01 failed, reason given by server:
  No such file or directory

```



could anyone point me to a solution for this?


many thanks

Nicolas

---

### Post by windependence on 2010-09-19
The syntax of the mount command is mount <what> <where>.
 
So if you want to mount the export under /mnt the command would be:
 
```
 
mount -t nfs4 /opt/nfs_exports/ISO01 /mnt

``` 
You don't want or need the IP in there on the localhost.
 
-Tim

---

### Post by jhwilliams on 2011-08-17
> **windependence said:**
> You don't want or need the IP in there on the localhost.

This does not solve the problem. Leaving out the hostname produces the error: ```
mount.nfs4: remote share not in 'host:dir' format

```

The solution is to rewrite the source path without the /path/to/exports/ portion:

```
mount -t nfs4 localhost:/ISO01/ /mnt/
```

That is, when you use a source like ```
localhost:/path/to/export
```, it gets interpreted by the server as ```
**localhost:/path/to/**path/to/export
```, because it resolves the hierarchy on its own, anyway.

---

