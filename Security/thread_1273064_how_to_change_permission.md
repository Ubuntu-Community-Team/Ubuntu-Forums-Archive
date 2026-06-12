---
title: "how to change permission???"
date: 2009-09-23
forum: Security
---

### Post by Myronray on 2009-09-23
hey guy gud day to all

i cant open my squid access.log due of this how to change permission to full and readable? 

-rw-r----- 1 proxy proxy     0 2009-09-23 10:20 access.log
-rw-r----- 1 proxy proxy 13450 2009-09-23 11:02 cache.log
-rw-r----- 1 proxy proxy     0 2009-09-23 10:20 store.log


thank to all support

---

### Post by scrooge_74 on 2009-09-23
chown root:root  *.log

---

### Post by Myronray on 2009-09-23
still no luck :(

---

### Post by dvlchd3 on 2009-09-23
Full access for whom?  Full for your user, a system process, root?

---

### Post by etnlIcarus on 2009-09-23
- try sudoing to read the log

- try [chmod](http://en.wikipedia.org/wiki/Chmod#Usage).

---

### Post by koenn on 2009-09-23
> **scrooge_74 said:**
> chown root:root  *.log

hmmm ... if you chown root:root, and the log can only be written by its owner, will the proxy account (i.e. the squid process) still be able to write to the log files ? that's what they're for, no ?

---

### Post by koenn on 2009-09-23
> **Myronray said:**
> still no luck :(
how are you trying to read the logs ?

what happens if you do
```

sudo -i
tail /var/log/squid/access.log

exit

```

---

### Post by scrooge_74 on 2009-09-24
> **koenn said:**
> hmmm ... if you chown root:root, and the log can only be written by its owner, will the proxy account (i.e. the squid process) still be able to write to the log files ? that's what they're for, no ?

:lolflag: yup you are right I guess it should be squid:root

---

### Post by Sarmacid on 2009-09-24
```
sudo chmod +r *.log
```Should make the files readable by anyone.

You can also add your user to the proxy group and you will be able to read them.

---

### Post by scrooge_74 on 2009-09-24
Million ways to do things, that is the best part of this

---

### Post by etnlIcarus on 2009-09-24
> **Sarmacid said:**
> ```
sudo chmod +r *.log
```Should make the files readable by anyone.

Actually, I think (technically), that should be a+r.

---

