---
title: "VMware increase partition"
date: 2008-12-12
forum: Virtualisation
---

### Post by any.linux12 on 2008-12-12
Hi!

I need to increase my virtual machine running LAMP from 5GB to something like 10GB, but without losing data and without grafical tools couse it's running in a Ubuntu server 64bis without GUI.

any help??please

---

### Post by HermanAB on 2008-12-12
It is usually better to leave the VM small for easy backup and mount the data over NFS on the host or somewhere else, where it can be backed up separately.

Cheers,

Herman

---

### Post by any.linux12 on 2008-12-15
ok but my Virtual machines are servers

I need to merge two vmware hard disk but I can't maybe because isn't possible to merge two different harddisks

Maybe it's possible to do a raid between them????

---

### Post by Dedoimedo on 2008-12-15
Hi,

I would do it like this:
[http://ubuntuforums.org/showthread.php?p=6371787#post6371787](http://ubuntuforums.org/showthread.php?p=6371787#post6371787)

Only the other way around...

The way I would do it ... Create a 10GB virtual disk. Attach it. Boot from CloneZilla CD (inside virtual machine), image the first hard disk (5GB) and restore it to the second hard disk (10GB), and then remove the first hard disk.

You do not have to delete the file, merely "un-attach" it from the vm configurations.

Dedoimedo

---

