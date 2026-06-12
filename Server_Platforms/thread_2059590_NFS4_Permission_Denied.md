---
title: "NFS4 Permission Denied"
date: 2012-09-18
forum: Server Platforms
---

### Post by systemshq on 2012-09-18
Hello. I'm tying to access an NFS4 file share that I've set-up but all I keep getting is permission denied. On the server I have:-

```

/etc/exports

/export       192.168.122.0/255.255.255.0(rw,fsid=0,nohide,insecure,no_subtree_check)
/export/www   192.168.122.0/255.255.255.0(rw,nohide,insecure,no_subtree_check)

The permissions on /export and /export/www are 1777

/etc/idmap.conf

[General]
Verbosity = 0
Pipefs-Directory = /run/rpc_pipefs
# set your own domain here, if id differs from FQDN minus hostname
Domain = ameris.co.uk

[Mapping]
Nobody-User = nobody
Nobody-Group = nogroup


/etc/default/nfs-common
NEED_GSSD=no
NEED_IDMAPD=yes


/etc/default/nfs-kernel-server
# Number of servers to start up
# To disable nfsv4 on the server, specify '--no-nfs-version 4' here
RPCNFSDCOUNT=8

# Runtime priority of server (see nice(1))
RPCNFSDPRIORITY=0

# Options for rpc.mountd.
# If you have a port-based firewall, you might want to set up
# a fixed port here using the --port option. For more information,
# see rpc.mountd(8) or http://wiki.debian.org/SecuringNFS
# To disable NFSv4 on the server, specify '--no-nfs-version 4' here
RPCMOUNTDOPTS=--manage-gids

# Do you want to start the svcgssd daemon? It is only required for Kerberos
# exports. Valid alternatives are "yes" and "no"; the default is "no".
NEED_SVCGSSD=

# Options for rpc.svcgssd.
RPCSVCGSSDOPTS=

# Options for rpc.nfsd.
RPCNFSDOPTS=

/etc/fstab
/var/www	/export/www	none	rw,bind		0	0


On the client:-

/etc/idmap.conf

[General]
Verbosity = 0
Pipefs-Directory = /run/rpc_pipefs
# set your own domain here, if id differs from FQDN minus hostname
Domain = ameris.co.uk

[Mapping]
Nobody-User = nobody
Nobody-Group = nogroup


/etc/default/nfs-common
NEED_GSSD=no
NEED_IDMAPD=yes


Then on the client as the root user:-

mount -t nfs4 vm2:/ /ecd /exports
cd /exports/
ls

www

which is correct but when I do:-

ls www

I get:-

ls: cannot open directory www: Permission denied

```

Can anyone please point me in the right direction? Many thanks

19/09/2012
----------
I can't believe it. My directories that were bound to /export/www didn't have any read permissions DOH!!! I've chmoded them to 775 and everything works!:)

---

### Post by sandyd on 2012-09-18
NFS4 uses userids, and gids, not usernames.

If you are accessing files over NFS4, make sure the uid/gid of the owner of the files on the NFS server and the uid/gid of the user you are accessing NFS on are the same.

You can check the UID/GID of a user by running
```

id *username*

```

---

### Post by systemshq on 2012-09-19
Many thanks for the reply. For some reason my server web directories didn't have read permission. I've given them 775 permissions and everything works as it should now.

---

