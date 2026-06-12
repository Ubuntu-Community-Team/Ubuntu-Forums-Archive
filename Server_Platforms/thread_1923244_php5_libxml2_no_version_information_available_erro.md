---
title: "php5 libxml2 no version information available error"
date: 2012-02-10
forum: Server Platforms
---

### Post by hdotnet on 2012-02-10
Hi there,

I keep getting hourly email messages from the root cron relating to php startup error messages:

Subject:
```
Cron <root@hostname>   [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -n 200 -r -0 rm
```

Message content (snipped)
```
php5: /usr/local/lib/libxml2.so.2: no version information available (required by php5)
```

Running php -v from a prompt reveals the same:
```

php -v
php: /usr/local/lib/libxml2.so.2: no version information available (required by php)
php: /usr/local/lib/libxml2.so.2: no version information available (required by php)
<snip>
PHP 5.3.3-1ubuntu9.9 with Suhosin-Patch (cli) (built: Feb  9 2012 06:37:37) 
Copyright (c) 1997-2009 The PHP Group
Zend Engine v2.3.0, Copyright (c) 1998-2010 Zend Technologies

```

I did an "apt-get upgrade php5-cli", hence the recent build date.

Doing a locate on libxml2.so reveals:

```

/usr/lib/libxml2.so.2
/usr/lib/libxml2.so.2.7.7
/usr/local/lib/libxml2.so
/usr/local/lib/libxml2.so.2
/usr/local/lib/libxml2.so.2.7.3
/var/src/libxml2-2.7.3/.libs/libxml2.so
/var/src/libxml2-2.7.3/.libs/libxml2.so.2
/var/src/libxml2-2.7.3/.libs/libxml2.so.2.7.3

```

```

DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=10.10
DISTRIB_CODENAME=maverick
DISTRIB_DESCRIPTION="Ubuntu 10.10"

```

FYI, 64bit install on RS cloud.
Linux cfpbbh1 2.6.35.4-rscloud #8 SMP Mon Sep 20 15:54:33 UTC 2010 x86_64 GNU/Linux

This has me baffled, and google isn't helping too much, nothing ubuntu specific at least, lots of cpanel/directadmin options but these arent installed... can anyone help?

Many thanks

---

