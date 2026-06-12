---
title: "squidGuard not blocking sites"
date: 2010-03-16
forum: Server Platforms
---

### Post by wsonar on 2010-03-16
not blocking sites

```



dbhome /var/lib/squidguard/db
logdir /var/log/squid



dest block {
       domainlist      block/domains
       urllist         block/urls
       redirect        http://localhost/blocked.html
}


acl {
        default {
                pass !block all
                rewrite  dmz
                redirect http://localhost/blocked.html
        }
}

```

under db I created a directory block where I created a domain file and a urls file dosen't seem to be working 

any help greatly appreciated

---

### Post by Dayofswords on 2010-03-16
you probably have read this already, but here
[https://help.ubuntu.com/community/SquidGuard](https://help.ubuntu.com/community/SquidGuard)

---

### Post by wsonar on 2010-03-17
> **Dayofswords said:**
> you probably have read this already, but here
[https://help.ubuntu.com/community/SquidGuard](https://help.ubuntu.com/community/SquidGuard)


well I didn't see this it was kinda helpfull but I still get this


```
denadmin@DEN-D107816:/etc/squid$ sudo squid -k reconfigure
squid: ERROR: Could not send signal 1 to process 16089: (3) No such process

```

before I could at least browse with the proxy now it won't browse at all

---

### Post by wsonar on 2010-03-17
when I have the lines for squidGuard in the squid.conf then squid quits working so it''s something with the squidguard permissions I think

---

### Post by wsonar on 2010-03-17
Can't figure out how to get past this

```
denadmin@DEN-D107816:/etc/squid$ sudo squid -k reconfigure
squid: ERROR: Could not send signal 1 to process 3100: (3) No such process

```

---

### Post by wsonar on 2010-03-17
when I do


```
sudo tail /var/log/squid/squidGuard.log
```

I get


```
2010-03-17 09:41:00 [3605] (squidGuard): Rewrite dmz is not defined in configfile /etc/squid/squidGuard.conf

```

---

### Post by wsonar on 2010-03-17
Sweet got it


I had this "rewrite  dmz" in the file I had to remove
```

dbhome /var/lib/squidguard/db
logdir /var/log/squid



dest block {
       domainlist      block/domains
       urllist         block/urls
       redirect        http://localhost/blocked.html
}


acl {
        default {
                pass !block all
               ## rewrite  dmz
                redirect http://localhost/blocked.html
        }
}


```

---

