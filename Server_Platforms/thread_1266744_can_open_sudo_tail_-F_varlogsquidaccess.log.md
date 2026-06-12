---
title: "can open sudo tail -F /var/log/squid/access.log"
date: 2009-09-15
forum: Server Platforms
---

### Post by Myronray on 2009-09-15
hey cant open the the access.log how to change permission to this file, anybody help

thanks

---

### Post by falconindy on 2009-09-15
I suspect if you did an `ls -l /var/log/squid/access.log` that the owner (root) would have read access already, but you can be certain of this by doing:
```
sudo chmod o+r /var/log/squid/access.log
```
Some commands are a little funky if you're running them through sudo and not actually at a root prompt. Have you tried that?

---

### Post by Myronray on 2009-09-15
> **falconindy said:**
> I suspect if you did an `ls -l /var/log/squid/access.log` that the owner (root) would have read access already, but you can be certain of this by doing:
```
sudo chmod o+r /var/log/squid/access.log
```
Some commands are a little funky if you're running them through sudo and not actually at a root prompt. Have you tried that?

im gonna try now hehe

---

### Post by Myronray on 2009-09-15
i check the permission it shows 
root@myron:/# ls -l /var/log/squid/access.log
-rw-r--r-- 1 proxy proxy 0 2009-09-15 11:20 /var/log/squid/access.log


falcon still no luck i follow your code but does not work :(
sudo chmod o+r /var/log/squid/access.log
then i tail -f access.log again does not open ohhh my

---

### Post by windependence on 2009-09-15
Try:

```
sudo chmod 755 /var/log/squid/access.log
sudo chown root:root /var/log/squid/access.log

```
-Tim

---

