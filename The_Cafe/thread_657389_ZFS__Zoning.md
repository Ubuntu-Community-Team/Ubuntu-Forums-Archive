---
title: "ZFS / Zoning"
date: 2008-01-03
forum: The Cafe
---

### Post by evil316 on 2008-01-03
Does Ubuntu or any other Linux distro have any plans to make use of ZFS or of zoning such as what Solaris 10 does?

---

### Post by Erunno on 2008-01-03
There's a userspace port of ZFS for Linux ([http://www.wizy.org/wiki/ZFS_on_FUSE]("http://www.wizy.org/wiki/ZFS_on_FUSE")) but it's still in a beta stage. ZFS can't be implemented in the Linux kernel due to incompatible licenses and, as far as I know, due to disagreements on filesystem design.

Even if the FUSE version would come out of beta stage one day I seriously doubt that it would be ever used as default due to ext3 and future versions being more or less the "official" Linux filesystem and therefore developed by the kernel folk. It's probably safer to stay with it.

---

### Post by evil316 on 2008-01-03
Last I heard ZFS wasn't even bootable yet.

---

### Post by zekopeko on 2008-01-03
[http://en.wikipedia.org/wiki/Btrfs](http://en.wikipedia.org/wiki/Btrfs)

the future?

---

### Post by evil316 on 2008-01-03
> **zekopeko said:**
> [http://en.wikipedia.org/wiki/Btrfs](http://en.wikipedia.org/wiki/Btrfs)

the future?

Hmmm, that's interesting!  I think I may have seen a distro on distrowatch the other day that uses that.  I remember it saying it used a new tree structure.  Can't remember the name of the distro though.

---

### Post by BOBSONATOR on 2008-01-03
Ist ZFS going to go on..



(looks around)



Leopard?

---

### Post by maniacmusician on 2008-01-03
> **BOBSONATOR said:**
> Ist ZFS going to go on..



(looks around)



Leopard?
[http://www.informationweek.com/news/199903281](http://www.informationweek.com/news/199903281)

---

### Post by jinx099 on 2008-01-03
I tried ZFS-Fuse and it is very slow.  Definitely not worth it.  I do really want to use ZFS on my file-server, I'll probly start a thread about it later.  Looks like the only options to do that are Solaris and FreeBSD.  ZFS will be bootable soon (if it isn't already) with Sun's Project Indiana.

I think its really sad that we cant use ZFS on linux due to license incompatibility.

---

