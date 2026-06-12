---
title: "Weird &quot;No space left on device&quot; Error on Lucid VPS"
date: 2011-03-04
forum: Server Platforms
---

### Post by MegaCrash57 on 2011-03-04
Ubuntu 10.04.2 LTS
Kernel: 2.6.32-24-server


I can't determine what is causing this exactly,
sometimes it happens if I try writing to a file that already exists,
other times it happens when I try to write a file (however the size doesn't seem to matter).

```
# df -hT
Filesystem    Type    Size  Used Avail Use% Mounted on
/dev/vda1     ext4     46G   31G   14G  70% /
none      devtmpfs    243M  132K  243M   1% /dev
none       debugfs     46G   31G   14G  70% /var/lib/ureadahead/debugfs
none         tmpfs    247M     0  247M   0% /dev/shm
none         tmpfs    247M   76K  247M   1% /var/run
none         tmpfs    247M     0  247M   0% /var/lock
none         tmpfs    247M     0  247M   0% /lib/init/rw
```

Now, its saying there's 14GB free, and I can't find anything that could cause this.
Never encountered this sorta problem before so I'm stumped, any help would be greatly appreciated.

---

### Post by wongo888 on 2011-03-04
I'd open a support ticket with your ISP.

---

### Post by samosamo on 2011-03-05
Welcome to the forums. It seems you have run out of inodes.  The reason is most likely an out of control app writing tons of small files.

Post the output of:
```
$ df -i
```

---

### Post by MegaCrash57 on 2011-03-10
It seems your right, thanks for your help
```
# df -i
Filesystem            Inodes   IUsed   IFree IUse% Mounted on
/dev/vda1            3055616 3055466     150  100% /
none                   62086     498   61588    1% /dev
none                   63194       1   63193    1% /dev/shm
none                   63194      45   63149    1% /var/run
none                   63194       2   63192    1% /var/lock
none                   63194       1   63193    1% /lib/init/rw
```

---

### Post by kupsztal on 2012-08-10
> **MegaCrash57 said:**
> It seems your right, thanks for your help


So what is the solution for such situation ?

---

### Post by LHammonds on 2012-08-10
> **kupsztal said:**
> So what is the solution for such situation ?

[http://stackoverflow.com/questions/653096/howto-free-inode-usage](http://stackoverflow.com/questions/653096/howto-free-inode-usage)

[http://www.nzlinux.com/2010/06/inode-problems-and-full-disks/](http://www.nzlinux.com/2010/06/inode-problems-and-full-disks/)

[http://www.gossamer-threads.com/lists/netapp/toasters/7148](http://www.gossamer-threads.com/lists/netapp/toasters/7148)

[http://www.ibm.com/developerworks/aix/library/au-speakingunix14/](http://www.ibm.com/developerworks/aix/library/au-speakingunix14/)

---

