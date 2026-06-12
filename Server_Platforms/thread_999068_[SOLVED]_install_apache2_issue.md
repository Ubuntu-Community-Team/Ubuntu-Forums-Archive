---
title: "[SOLVED] install apache2 issue"
date: 2008-12-01
forum: Server Platforms
---

### Post by gishaust on 2008-12-01
I installed apache a little while ago and while playing with it I broke it really badly. That did not really worry me as it was a development server. But now I want to install it again and it keeps saying the following
```

Selecting previously deselected package apache2.

```
 I think it is looking at how it was installed and installing that way. But it will never work. So I want to do a complete fresh install. How do I make it do that?

---

### Post by gishaust on 2008-12-01
Ok i think there is something wrong with the package. after the install it tells me the following,

```

Need to get 44.6kB of archives.
After this operation, 102kB of additional disk space will be used.
Get:1 http://au.archive.ubuntu.com hardy-updates/main apache2 2.2.8-1ubuntu0.3 [44.6kB]
Fetched 44.6kB in 3s (13.7kB/s) 
Selecting previously deselected package apache2.
(Reading database ... 146478 files and directories currently installed.)
Unpacking apache2 (from .../apache2_2.2.8-1ubuntu0.3_all.deb) ...
Setting up apache2 (2.2.8-1ubuntu0.3) ..

```

apache is a lot larger than 102kb installed? It is not looking at the old install its not installing have i got this right?

---

### Post by gishaust on 2008-12-01
ha I was right I found this this is the aptitude log
```


[INSTALL] apache2
===============================================================================

Log complete.
Aptitude 0.4.9: log report
Mon, Dec  1 2008 16:49:22 +1100

IMPORTANT: this log only lists intended actions; actions which fail due to
dpkg problems may not be completed.

Will install 0 packages, and remove 1 packages.
102kB of disk space will be freed
===============================================================================
[REMOVE] apache2
===============================================================================

Log complete.
```

It never installs but how do I fix it?

---

### Post by cdenley on 2008-12-01
apache2 is a meta-package. It doesn't really have anything except readme files and copyright info. The bulk of the actual server is probably in apache2.2-common and apache2-mpm-preform or apache2-mpm-worker. Do you want to remove all your configuration as well?

```

sudo apt-get purge apache2 apache2.2-common apache2-* libapache2-*

```

---

### Post by gishaust on 2008-12-01
Thanks it worked first go and reinstall properly first go. I had been purging it but I did not know about apache2.2-common apache2-* libapache2-* where do I go to do some reading on it? =) thanks again

---

### Post by cdenley on 2008-12-01
> **gishaust said:**
> where do I go to do some reading on it?

[http://packages.ubuntu.com/](http://packages.ubuntu.com/)
[http://packages.ubuntu.com/intrepid/apache2](http://packages.ubuntu.com/intrepid/apache2)
Notice it has a dependency:
> 
apache2-mpm-worker  (>= 2.2.9-7ubuntu3)
or apache2-mpm-prefork (>= 2.2.9-7ubuntu3)
or apache2-mpm-event (>= 2.2.9-7ubuntu3)

which means one of those 3 must be installed before apache2 can be. Then each of those will have their own dependencies, including apache2.2-common.

The asterisks in the command I gave you is a wildcard. "apache2-*" means it will purge any packaging with a name starting with "apache2-".

---

### Post by gishaust on 2008-12-01
thanks

---

