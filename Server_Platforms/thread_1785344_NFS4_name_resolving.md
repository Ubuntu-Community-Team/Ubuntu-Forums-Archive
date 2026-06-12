---
title: "NFS4 name resolving"
date: 2011-06-18
forum: Server Platforms
---

### Post by pinus on 2011-06-18
I wanted to set up a small file server. Since it is not acceptable for me to have the same UID on all clients I decided to use NFS4 which should be able to solve that. I started with Ubuntu 11.04.

What I did manage is access files (rw) if I have the same UID on client and server. If they differ I get an error message.

I find that a bit surprising since I have the most basic setup which should work without trouble.

/etc/exports on the server
```
/data 10.0.0.0/24(rw,sync,fsid=0,crossmnt,no_subtree_check)
```

/etc/idmapd.conf on client and server
```
[General]
Verbosity = 0
Pipefs-Directory = /var/lib/nfs/rpc_pipefs
Domain = local
[Mapping]
Nobody-User = nobody
Nobody-Group = nogroup
```

Domain names on the client
```
root@zesi:/# hostname
zesi
root@zesi:/# dnsdomainname 
local
```

But I get strange syslog entries
```
Jun 13 21:43:42 zesi rpc.idmapd[10766]: nss_getpwnam: name '0' does not map into domain 'local'
Jun 13 21:43:47 zesi rpc.idmapd[10766]: nss_getpwnam: name '1001' does not map into domain 'local'
Jun 13 21:43:47 zesi rpc.idmapd[10766]: nss_getpwnam: name '1002' does not map into domain 'local'
Jun 13 21:43:47 zesi rpc.idmapd[10766]: nss_getpwnam: name '1003' does not map into domain 'local'
Jun 13 21:43:47 zesi rpc.idmapd[10766]: nss_getpwnam: name '1004' does not map into domain 'local'
```

Does anybody know internals of the rpc.idmapd and can explain the function nss_getpwnam? Whats wrong here?

---

