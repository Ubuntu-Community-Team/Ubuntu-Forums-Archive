---
title: "NFS client-server issues"
date: 2006-02-11
forum: Server Platforms
---

### Post by bjhess on 2006-02-11
**The problem:**

I can mount my NFS share on a client machine.  I can see at a depth of one folder from the mountpoint, but no further down.

**The configuration:**

My NAS is running all NFS "stuff" as best as I can tell.  I've added information to several files as specified in [these]("https://wiki.ubuntu.com/NFSServerHowTo") [various]("http://nfs.sourceforge.net/nfs-howto/") [HOWTO's]("https://wiki.ubuntu.com/FindPage?action=fullsearch&titlesearch=1&value=nfs").

So I'm starting to think the problem lies in one of two places.  Either a) the fact that I'm sharing the same pieces of the file system with Samba or b) the fact that I'm mounting a share on my client that is itself comprised of mounts on the server.

The NAS has multiple hard drives to store media content.  Each partition is mounted at /mediamnt/hda4, /mediamnt/hdd1, etc.  My goal in setting up NFS is to allow my ripping machine to transfer files >2 GB, which is apparently a limitation of Samba.  So I set up my export file to basically share all of these content drives giving my ripping machine rw access.  Pretty simple:

```
/mediamnt 192.168.xxx.xxx(rw,async) 192.168.xxx.xxx(ro,async)
```

And I was able to mount this share pretty easily with the client at /mnt/mediawrite.  However, I could only browse to the level of /mnt/mediawrite and see folders in there (hda4, hdd1, etc).  When trying an ls /mnt/mediawrite/hdd1 I get no results.  I've tried two separate client machines with the same results.

For a test I shared the / of my NAS.  I was able to browse around with that share quite extensively.  Of course, when I tried to browse through any mountpoints I was stopped at the pass.

So - is there an issue with browsing a mount of a mount?  I wouldn't think it would matter because as far as the client is concerned he is only looking at a filesystem.

And I suppose a somewhat related question would be - is it possible to just go back to Samba and get large file transfers working?  (I suspect Samba can read large files - just not write them.)  It'd be nice to only have to maintain a single networking environment.  (Samba is necessary in my case for supplying an Xbox with XBMC.)

---

