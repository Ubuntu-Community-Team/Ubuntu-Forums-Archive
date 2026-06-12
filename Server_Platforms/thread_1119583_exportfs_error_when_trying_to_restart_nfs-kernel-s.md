---
title: "exportfs error when trying to restart nfs-kernel-server"
date: 2009-04-08
forum: Server Platforms
---

### Post by reza81 on 2009-04-08
Hello,

I have installed a nfs server on ubuntu 8.10 server to map a nfs share to my vmware esx 3.x

the linked directory is /vm

It connected but i get a error when i try to copy big files from another datastore.

I also get an error wheb i try to restart the nfs-kernel-server
```

xx@xx:/$ sudo /etc/init.d/nfs-kernel-server restart
exportfs: /etc/exports [1]: Nether 'subtree' or 'no_subtree_check' specified for export '10.37.0.3/16:/mount/vm'.
assuming default behaviour ('no_subtree_check').
NOTE: this default has chaged since nfs-utils version 1.0.x

```
but it still starts the demon!

my exports file:
/mount/vm/    10.37.0.3/16(rw,no_root_squash,async)

/mountvm/ is chmod 777

what should i do?

---

### Post by reza81 on 2009-04-08
solved:

Needed to chenge /etc/exports 
to:
/mount/vm/ 10.37.0.3/16(rw,no_root_squash,no_subtree_check,async)

---

