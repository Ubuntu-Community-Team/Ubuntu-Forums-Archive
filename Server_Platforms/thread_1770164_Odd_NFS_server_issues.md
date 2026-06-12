---
title: "Odd NFS server issues"
date: 2011-05-28
forum: Server Platforms
---

### Post by MakOwner on 2011-05-28
I have a machine that acts as an NFS server on my network - it's at 10.04.2 LTS and does NFS exports of a software raid array.

The export file has some overlapping exports with different permissions for different hosts like this:
```

/media/md0p1	host1(rw,sync,no_subtree_check,no_root_squash)
/media/md0p1    host2(ro,sync,no_subtree_check,no_root_squash)
/media/md0p1/Movies	*(ro,sync,no_subtree_check,insecure,hide)
/media/md0p1/TVShows	*(ro,sync,no_subtree_check,insecure,hide)

```

When the box boots up, sometimes only the * exports are active.
If I do reload of the nfs server, and then the exports show up as I expect them too.

Anyone seen this before, where should I be looking to figure out why this happens?

---

### Post by ralfarof on 2011-05-28
> **MakOwner said:**
> I have a machine that acts as an NFS server on my network - it's at 10.04.2 LTS and does NFS exports of a software raid array.

The export file has some overlapping exports with different permissions for different hosts like this:
```

/media/md0p1	host1(rw,sync,no_subtree_check,no_root_squash)
/media/md0p1    host2(ro,sync,no_subtree_check,no_root_squash)
/media/md0p1/Movies	*(ro,sync,no_subtree_check,insecure,hide)
/media/md0p1/TVShows	*(ro,sync,no_subtree_check,insecure,hide)

```

When the box boots up, sometimes only the * exports are active.
If I do reload of the nfs server, and then the exports show up as I expect them too.

Anyone seen this before, where should I be looking to figure out why this happens?


have you tried using IP instead of DNS names? Could be a DNS issue

---

### Post by MakOwner on 2011-05-29
> **ralfarof said:**
> have you tried using IP instead of DNS names? Could be a DNS issue

I'm positive both forward and reverse DNS lookups are correct - thing is, the actual exports list of the NFS server is what's affected - not connectivity.

showmount -e from the NFS server host or another host on the network will look like this after a reboot
```

showmount -e shuttle
Exports list on shuttle:
/media/md0p1/TVShows                *
/media/md0p1/Movies                 *

```

Then like this after the reload

```

macmini:~ dale$ showmount -e shuttle
Exports list on shuttle:
/media/md0p1/TVShows                *
/media/md0p1/Movies                 *
/media/md0p1                        host1 host2

```

It looks like for some reason the complete exports file isn't processed for some reason.

---

