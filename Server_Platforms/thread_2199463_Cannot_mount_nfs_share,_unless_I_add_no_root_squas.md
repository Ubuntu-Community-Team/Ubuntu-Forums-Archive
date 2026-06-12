---
title: "Cannot mount nfs share, unless I add no_root_squash"
date: 2014-01-14
forum: Server Platforms
---

### Post by ianw1974 on 2014-01-14
Hi,

I'm having problems with nfs.  Previously with Ubuntu 10.04, I had the following, and it was working:

```
/home/ian/Downloads 192.168.1.0/24(rw,async,no_subtree_check,anonuid=1000,anongid=1000)
```

anonuid/anongid is for user "ian".  This means that when I mount, everything has my uid/gid under my directory.  So all was OK.  I then updated my system, now running Ubuntu 13.10.  It has stopped working.  It denies access.  The only way I can get my share to mount is to then change it, and add no_root_squash.

```
/home/ian/Downloads 192.168.1.0/24(rw,async,no_subtree_check,anonuid=1000,anongid=1000,no_root_squash)
```

then my nfs share will mount.  But I don't want this, because then all files uploaded to my area has uid/gid of 0, which is root.  I want it to have my uid/gid like previous.  Even if I add all_squash and edit /etc/idmapd.conf to use my login "ian" instead of nobody/nogroup, it still doesn't work.

How can I get it to work like previous?

---

### Post by SeijiSensei on 2014-01-14
Since I always mount shares as root with no_root_squash, I cannot answer your question.  However, even in that case, if you create a file on the share as user ian, it will have ian's permissions.  You just need to make sure that ian can normally write into the share on the server.

---

