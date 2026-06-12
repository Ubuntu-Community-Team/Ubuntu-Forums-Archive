---
title: "NFS hardly working after upgrade from 10.04 to 12.04"
date: 2013-06-10
forum: Server Platforms
---

### Post by dannew on 2013-06-10
Hi!

I have a fileserver running Ubuntu and a bunch of clients mounting shares over NFS from the server.

It was running fine on ubuntu 10.04 but since I upgraded to 12.04 the performance is horrible, atop shows the disks are busy, writes are incredibly slow, copying a GB can take hours. Writing files locally works fine, I have also tried copying files over scp which also works fine, so I think the problem is isolated to NFS.

Any ideas what could be causing this?

---

### Post by SeijiSensei on 2013-06-11
Does the server have "async" among the options?  Also there seems to be a number of people reporting NFS problems since the default protocol changed in 12.04 from v3 to v4.  Browse this forum a bit for other reports on NFS in 12.04; you might some help there.

---

### Post by dannew on 2013-06-12
No, these are the options set in /etc/exports:
(rw,sync,no_root_squash)

And yes, I have found lots of people with NFS problems in 12.04, but a lot more problems then answers, that's why I tried starting a thread about this.

---

### Post by SeijiSensei on 2013-06-12
Try using async for starters.  Unless your server is subject to random crashes or power outages, it is perfectly safe and tends to be much faster than sync.

---

### Post by dannew on 2013-06-12
I can try that, but I need a speedup of about 1000 times to reach normal speeds, will async do that? I think that I am looking for a real problem, not an optimization.

---

### Post by SeijiSensei on 2013-06-12
Well, most of the discussions I've seen about 12.04 suggest reverting to NFSv3 as a possibility.  Have you tried that?

---

### Post by dannew on 2013-06-13
No, I haven't, do you have any link to more info on how to use NFSv3? Do I set that option on server or the client?

---

### Post by SeijiSensei on 2013-06-13
On the server, edit /etc/default/nfs-kernel-server like this:

```

# To disable NFSv4 on the server, specify '--no-nfs-version 4' here
RPCMOUNTDOPTS=--manage-gids

```

So you would enter
```
RPCMOUNTDOPTS="--manage-gids --no-nfs-version-4"
```

and restart the NFS service.

I'd still use "async" as well.

---

