---
title: "NFS mount being squashed: Why?"
date: 2010-01-23
forum: Security
---

### Post by noah++ on 2010-01-23
Hi,

Our problem arose when we upgraded to a new version of Wine to gain compatibility with a Windows program. The new version checks that its working directory is owned by the executing user. If it isn't, then Wine refuses to run.

We mount home directories over NFS. When we export, we squash root only -- we don't squash all. Yet from the clients' points of view, users' home directories are always owned by nobody/nogroup (65534/65534). I believe nothing in our *exports* or *fstab*s would cause that.
```
#Client /etc/fstab line
192.168.1.1:/   /FileServer     nfs4    proto=tcp,sec=sys,hard,intr,rsize=3276800
``````
#Server /etc/exports
/home/nfs-export/       192.168.1.0/24(rw,fsid=0,root_squash,sync)
```My only idea: Because **/home/nfs-export** is root-owned, all its subdirectories look root-owned upon export. The home directory that the client mounts is actually **/home/nfs-export/Users/*username***. So does the client's fstab need explicit, nested mounts of each individual home directory? Or how else should I proceed?

---

### Post by falconindy on 2010-01-24
This isn't a matter of the user being squashed. Squashing means that a user by the name of 'foo' means that they will be refused the same permissions as user of the same name 'foo' on the remote system.

Users and groups are exported by name. If you're not part of the same NIS domain and you try to export the share owned by a user that does not exist on the remotely connected client, it is mapped to 'nobody'.

You *might* be able to get away with something as simple as creating an account for each user on the server.

---

### Post by noah++ on 2010-01-24
Thank you for your response.

All of our users and groups exist only on the server. All workstations authenticate to the server by NIS. Taking a user/UID and its group/GID that exist on the server, I made identical entries in a client's local passwd and group files. It didn't make a difference.

I remember reading somewhere that the new NFS versions export by name, whereas older ones do it by ID number. We just upgraded the clients to 9.10, with the server still on 8.10. Is that likely to be the problem? (We'd rather not upgrade the server!)

---

### Post by falconindy on 2010-01-24
> **noah++ said:**
> Thank you for your response.

All of our users and groups exist only on the server. All workstations authenticate to the server by NIS. Taking a user/UID and its group/GID that exist on the server, I made identical entries in a client's local passwd and group files. It didn't make a difference.

I remember reading somewhere that the new NFS versions export by name, whereas older ones do it by ID number. We just upgraded the clients to 9.10, with the server still on 8.10. Is that likely to be the problem? (We'd rather not upgrade the server!)
Your mount entries on both server and client side seem to support the idea that they're nfs4 mounts (I'm not sure if you can mount an nfs3 mount with the nfs4 driver). What NFS-related services are you running on the server? The major difference between the two setups is that the older version uses portmap versus rpcbind on the newer.

---

### Post by noah++ on 2010-01-25
Does this answer your question?

_**Server**_```
daemon    7571     1  0 08:37 ?        00:00:00 /sbin/portmap
statd     7597     1  0 08:37 ?        00:00:00 /sbin/rpc.statd
root      7602     2  0 08:37 ?        00:00:00 [rpciod/0]
root      7619     1  0 08:37 ?        00:00:00 /usr/sbin/rpc.idmapd
root      8428     1  0 08:37 ?        00:00:00 /usr/sbin/rpc.mountd
```_**Client**_```

daemon     841     1  0 08:38 ?        00:00:00 portmap
root       805     2  0 08:38 ?        00:00:00 [rpciod/0]
root       806     2  0 08:38 ?        00:00:00 [rpciod/1]
statd      875     1  0 08:38 ?        00:00:00 rpc.statd -L
root       959     1  0 08:38 ?        00:00:00 rpc.idmapd
```

---

### Post by noah++ on 2010-02-22
Steps taken:

1. NFS server: **/etc/hostname**, changed contents from local hostname to FQDN. Restarted **nfs-common**.
2. Some NFS clients: **/etc/idmapd.conf** had been unconfigured. Added proper **domain =** . Rebooted.

---

### Post by arune on 2013-01-16
Thank you! This solved the issue for me aswell.

---

### Post by pla on 2013-02-13
Thanks @noah++. You solution resolved my NFS permission issue.

---

### Post by codemaniac on 2013-02-14
As per the Ubuntu Forums Code of Conduct, please do not post in threads more than one year old.

Thread closed.

Thanks.

---

