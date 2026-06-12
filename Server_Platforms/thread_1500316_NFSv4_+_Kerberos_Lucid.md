---
title: "NFSv4 + Kerberos Lucid"
date: 2010-06-03
forum: Server Platforms
---

### Post by Lucky. on 2010-06-03
Gah, frustration mounting!

Has anybody gotten NFSv4 + Kerberos to work in Lucid?  I've followed [this tutorial](https://help.ubuntu.com/community/NFSv4Howto) over and over, with no luck.  I wish I could post my error message, but right now it's probably irrelevant as I've trashed my server after a dozen tweaks trying to get this to work.

I'll start over one more time and see if I can post the error message & log results.

For now I'm really just wondering if anybody has gotten this to work at all.  I'd feel better if I knew this write-up was legitimate.

EDIT:  After starting over, it appears the official message is:

```

mount.nfs4: mounting <myserver>:<myshare> failed, reason given by server:
No such file or directory

```

---

### Post by Lucky. on 2010-06-03
Never mind, found the answer on [this page](http://forums.fedoraforum.org/showthread.php?t=235212).

For testing purposes, I kept specifying a server path when I'd try to mount.  So I'd write something like:

```

mount -t nfs4 -o sec=krb5 myserver:/mypath/tostuff /mnt/localmountpoint

```

But specifying /mypath/tostuff was no good according to the comment on the other board:

> 
For NFSv4 you DO NOT specify the server path - EVER. So assuming on your server in /etcportfs you have "fsid=0" then the correct mount command is:
mount -t nfs4 localhost:/ /media/tonlist

**NOT** localhost:/home. but localhost:/

Otherwise you need to specify the fsid.as a integer or uuid.


After I tried the following:

```

mount -t nfs4 -o sec=krb5 myserver:/ /mnt/localmountpoint

```

I was in good shape.

---

