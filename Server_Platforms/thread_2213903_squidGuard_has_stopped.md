---
title: "squidGuard has stopped"
date: 2014-03-29
forum: Server Platforms
---

### Post by lee16 on 2014-03-29
Hi Guys

I am using ubuntu 10.04 LTS server. Running squid with squidGuard for the first time. Both  squid and SquidGuard are running after configuration.

However, I have a problem updating my squidguard db files. When I run Either squidGuard -C ALL or  squidGuard /etc/squid/squidGuard.conf -C all , squidGuard will stop running. Does anyone know why? I have pasted a copy of my configuration and log file

I have adjusted my file permissions just like [https://help.ubuntu.com/community/SquidGuard](https://help.ubuntu.com/community/SquidGuard)

My log file /var/log/squid/squidguard.log

```
2014-03-29 20:49:12 [873] init domainlist /var/lib/squidguard/db/blacklist/domains
2014-03-29 20:49:12 [873] loading dbfile /var/lib/squidguard/db/blacklist/domains.db
2014-03-29 20:49:12 [873] squidGuard 1.2.0 started (1396097352.420)
2014-03-29 20:49:12 [873] db update done
2014-03-29 20:49:12 [873] squidGuard stopped (1396097352.420)
```

My SquidGuard Configuartion

```
dbhome /var/lib/squidguard/db
logdir /var/log/squid

dest bad {
        domainlist blacklist/domains
}

acl {
        default {
                pass !bad all
                redirect http://www.google.com
        }
}
```

---

### Post by houstonbofh on 2014-03-29
This is probably not your problem, but...

10.04 is very out of date, and as a consequence it gets less mind share.  (As is the version of Squid available in 10.04)  I would start by moving to 12.04, or perhaps 14.04.  The newer versions may resolve the problem, but if not, you will have many more people active, and able to help you.

---

### Post by lee16 on 2014-03-30
There is no problem with the program, just that there might be some mistake/configuration that I unable to figure out.
 I have seen it work fine with on other servers

I will give 12.10 LTS A go though, see if it works.

---

### Post by lisati on 2014-03-30
AFAIK, 12.10 wasn't LTS, but 12.04 was.

---

