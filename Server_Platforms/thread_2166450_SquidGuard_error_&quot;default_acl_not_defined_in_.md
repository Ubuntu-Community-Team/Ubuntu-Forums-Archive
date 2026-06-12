---
title: "SquidGuard error &quot;default acl not defined in configfile&quot;"
date: 2013-08-09
forum: Server Platforms
---

### Post by nativehound on 2013-08-09
Hello, ive been trying to setup SquidGuard in kubuntu 12.04.2.
When I run the command to make the db it throws an error.

```
sudo squidGuard -d -b -P -C all
```

I get this output:
 
```
2013-08-09 09:23:14 [6142] squidGuard: default acl not defined in configfile  /etc/squid/squidGuard.conf
2013-08-09 09:23:14 [6142] Going into emergency mode

```

The squidGuard config file looks like this:

```

#
# CONFIG FILE FOR SQUIDGUARD
#
# Caution: do NOT use comments inside { }
#

dbhome /var/lib/squidguard/db
logdir /var/log/squid

dest ads {
        log              ads
        domainlist  ads/domains
        urllist          ads/urls

}

acl  {
        default {
                pass !ads all
                redirect 302:http://www.google.com
        }
}

```

Squid3 is working and HITTING the cache.

The permissions are set to proxy : proxy.

The Ver. of  Squid 3.1.19-1ubuntu3.12.04.2 and  SquidGuard 1.4-4build1

Any help would be appreciated....

---

### Post by nativehound on 2013-08-10
I got it to work. Uninstalled SquidGuard 1.4-4build1 and then installed SquidGuard 1.5beta from source.
To install SquidGuard
 
```
./configure --with-db=/usr/local/db-6.0.20 --with-squiduser=proxy
```

```
make
```

```
sudo make install
```


I used this guide

[http://www.danscourses.com/Linux-Fundamentals/install-a-configure-squidguard-in-ubuntu.html]("http://www.danscourses.com/Linux-Fundamentals/install-a-configure-squidguard-in-ubuntu.html")

---

