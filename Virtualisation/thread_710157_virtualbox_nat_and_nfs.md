---
title: "virtualbox nat and nfs"
date: 2008-02-28
forum: Virtualisation
---

### Post by tekknokrat on 2008-02-28
Hi all,

I am posting this because i am not sure its related virtualbox problem or an
inter ubuntu  one...

I have vb running on gutsy host with feisty as the virtual machine os because I need it for some test scenario.
I want the vm to mount some gutsy folder via nfs. Due to several problems with bridging mode is only nat mode possible.
Problem is i always getting permission denied when I try mounting.
So it seems to me that server is accessible.

relevant settings:

server:

/etc/exports

```
/backup         192.168.2.0/24(rw,no_root_squash,subtree_check,sync)

```
this is the network the vb nat engine is using

/etc/fstab

```
/dev/vg/backup /backup  reiserfs        defaults        0       0
```

client:

/etc/fstab

```
tigger:/backup /nas/backup nfs defaults,noauto,intr,hard                                                                                        0       0

```

server message:
```

sudo mount tigger:/backup /nas/backup/ -t nfs
mount: tigger:/backup failed, reason given by server: Permission denied
```

/etc/defaults/nfs-common

```
STATDOPTS="--port 32765 --outgoing-port 32766"
```

this is the only line I changed

Please have a look in the thread I have posted in virtualbox forums
Theres also the config for portforwarding in vb.

[http://forums.virtualbox.org/viewtopic.php?t=4834&highlight=](http://forums.virtualbox.org/viewtopic.php?t=4834&highlight=)

---

