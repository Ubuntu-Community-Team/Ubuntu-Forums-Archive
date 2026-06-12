---
title: "Apache2 down after updated"
date: 2008-10-14
forum: Server Platforms
---

### Post by [pl]ice on 2008-10-14
Hi,
  got ubuntu LAMP, had ssl certificates and all was good. I did apt-get update, apt-get upgrate. Game over, my apache2.conf does not contain ssl options, certificates are gone, and apache won't start, its hanging at the /etc/init.d/apache2 start 

Any ideas? I'm bit annoyed :/

thanks

---

### Post by CoBPEZ on 2008-10-15
I have a similar problem. Apache2 startup scripts hangs, even if I do "apache2ctl stop". apt-get (or dpkg, if you like) hangs on all configuration that involves servers; postfix, ssh, you name it. I am clueless except for this strange "df -h" output:
```
Filesystem            Size  Used Avail Use% Mounted on
/dev/simfs             19G  3.3G   15G  19% /
/dev                  257M   16K  257M   1% /dev
tmpfs                 257M   28K  257M   1% /var/run
tmpfs                 257M     0  257M   0% /var/lock
tmpfs                 257M     0  257M   0% /dev/shm
df: `/dev/shm/var.run': No such file or directory
df: `/dev/shm/var.lock': No such file or directory
none                  257M     0  257M   0% /dev/shm
```

---

### Post by [pl]ice on 2008-10-15
yep, that what I mean. I might compile apache myself, and not trust ubuntu on updating it. But my certs are gone of hard drive... very strange!

---

### Post by CoBPEZ on 2008-10-15
The thing is that I think this goes deeper than apache2 problems.

---

