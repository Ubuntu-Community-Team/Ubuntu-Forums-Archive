---
title: "Something Eating HD Space"
date: 2010-06-04
forum: Server Platforms
---

### Post by teqsun on 2010-06-04
Ok, I am running Ubuntu 8.10 Server and have been doing fine for a while now.

Recently I ran into a problem when I would use "df -h" to find out hard drive space.


when I run this it says I am at 100% capacity on my main disk.

I deleted a few files then run df -h.  It still says 100% but every time i run the command the free space is diminishing.  I took a look using the command:

```
du -a /var | sort -n -r | head -n 10
```

which brought me to the following:
```
134926596       /var
132906692       /var/log
132883892       /var/log/gdm
75844756        /var/log/gdm/:0-greeter.log
47349596        /var/log/gdm/:0-greeter.log.1
9689368 /var/log/gdm/:1-greeter.log
1415912 /var/lib
660028  /var/lib/mysql
543256  /var/lib/mysql/ibdata1
502928  /var/cache

```

So I took a look in /var/log/gdm and this is what I found... Why on earth would a greeter log be taking up so much space?

```
root@hellcat:/var/log/gdm# ls -l
total 133283292
-rw-r--r-- 1 gdm  gdm  77997764608 2010-06-04 11:32 :0-greeter.log
-rw-r--r-- 1 gdm  gdm  48438624350 2010-05-17 00:42 :0-greeter.log.1

```

am I bone here do I have a rootkit?  has somebody hacked me?  I am pretty worried now.

---

### Post by teqsun on 2010-06-04
so I deleted the large files, and now my df -h seems to be solid.

Also removed gdm as well

```
root@hellcat:/var/log/gdm# df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1             229G  163G   55G  76% /

```

---

