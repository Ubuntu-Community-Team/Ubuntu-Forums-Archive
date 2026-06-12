---
title: "nfs problem lucid -&gt; hardy"
date: 2010-05-29
forum: Server Platforms
---

### Post by allanj on 2010-05-29
Hi

I have a hardy server with some website backups that i nfs mount from other servers. This works perfectly from hardy clients, but my first lucid client won't mount it, i have googled for an answer, but no luck.

The error message: 

#mount -t nfs 192.168.1.104:/opt/websites /backups -v
mount.nfs: timeout set for Sat May 29 10:25:38 2010
mount.nfs: text-based options: 'addr=192.168.1.104'
mount.nfs: mount(2): Protocol not supported
mount.nfs: trying 192.168.1.104 prog 100003 vers 3 prot UDP port 2049
mount.nfs: mount to NFS server '192.168.1.104:/opt/websites' failed: RPC Error: Success

On the hardy server i am using:
ii  nfs-user-server                       2.2beta47-23                          User space NFS server
ii  portmap                               6.0-4                                 The RPC portmapper

On the lucid client:
ii  libnfsidmap2                     0.23-2                            An nfs idmapping library
ii  nfs-common                       1:1.2.0-4ubuntu4                  NFS support files common to client and serve
ii  portmap                          6.0.0-1ubuntu2                    RPC port mapper

The "protocol not supported" could point to a missing module, but lsmod shows that the nfs kernel module is loaded.


Best regards
Allan Jacobsen

---

