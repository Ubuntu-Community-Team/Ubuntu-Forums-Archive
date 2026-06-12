---
title: "Installing FUSE and GlusterFS on 6.06"
date: 2008-04-25
forum: Server Platforms
---

### Post by Synchro on 2008-04-25
I'm trying to get a simple cluster/afr deployment of GlusterFS on 2 machines in order to support a redundant web front end. Each machine is to run both client and server, replicating to each other.

I've (apparently) successfully built and installed the Gluster client/server, modprobe tells me I have fuse.ko present, I've installed libfuse2 and libfuse-dev (standard packages). The glusterfsd server seems to work ok (I can telnet to it without errors), but the client fails because it can't find a fuse.so:

```
2008-04-24 15:50:25 E [xlator.c:120:xlator_set_type] xlator: dlopen(/usr/local/lib/glusterfs/1.3.8pre6/xlator/mount/fuse.so): /usr/local/lib/glusterfs/1.3.8pre6/xlator/mount/fuse.so: cannot open shared object file: No such file or directory
2008-04-24 15:50:25 E [glusterfs.c:547:main] glusterfs: Initializing graph failed

```
Any ideas how to fix that?

I'm asking on here as I suspect that something is astray with my fuse libs rather that anything else, I've no idea how to test that easily.

---

