---
title: "seg fault with apache2 (ssl) + php5-curl"
date: 2010-06-03
forum: Server Platforms
---

### Post by sgoranov on 2010-06-03
Hello,
I'm trying to run apache2 with mod_ssl and php support and I need curl too. When php5-curl is installed apache doesn't work with ssl and I've got this one in error.log:

```
[Thu Jun 03 10:00:39 2010] [notice] child pid 26013 exit signal Segmentation fault (11)
[Thu Jun 03 10:00:39 2010] [notice] child pid 26014 exit signal Segmentation fault (11)
```

It's strange because it works well without ssl. The problem occures only when I'm trying to access and SSl page, doesn't matter if it's a html page or php file. I'm using Ubuntu 10.06 Desktop version which is x64. Bellow are the packages which I've got installed related to apache php and curl. Any suggestions are welcome! Thanks in advance!

```
# dpkg --list|grep apache
ii  apache2-mpm-prefork                  2.2.14-5ubuntu8                                 Apache HTTP Server - traditional non-threade
ii  apache2-utils                        2.2.14-5ubuntu8                                 utility programs for webservers
ii  apache2.2-bin                        2.2.14-5ubuntu8                                 Apache HTTP Server common binary files
ii  apache2.2-common                     2.2.14-5ubuntu8                                 Apache HTTP Server common files
ii  libapache2-mod-php5                  5.3.2-1ubuntu4.2                                server-side, HTML-embedded scripting languag


# dpkg --list|grep curl
ii  gnupg-curl                           1.4.10-2ubuntu1                                 GNU privacy guard - a free PGP replacement (
ii  libcurl3                             7.19.7-1ubuntu1                                 Multi-protocol file transfer library (OpenSS
ii  libcurl3-gnutls                      7.19.7-1ubuntu1                                 Multi-protocol file transfer library (GnuTLS
ii  php5-curl                            5.3.2-1ubuntu4.2                                CURL module for php5
ii  python-pycurl                        7.19.0-3                                        Python bindings to libcurl

# dpkg --list|grep php
ii  libapache2-mod-php5                  5.3.2-1ubuntu4.2                                server-side, HTML-embedded scripting languag
ii  php5                                 5.3.2-1ubuntu4.2                                server-side, HTML-embedded scripting languag
ii  php5-common                          5.3.2-1ubuntu4.2                                Common files for packages built from the php
ii  php5-curl                            5.3.2-1ubuntu4.2                                CURL module for php5

```

P.S.
I successfully compiled php5 from source, but the problem still exists so probably it's somewhere in apache?

---

### Post by doudenit on 2010-06-03
> **sgoranov said:**
> Hello,
I'm trying to run apache2 with mod_ssl and php support and I need curl too. When php5-curl is installed apache doesn't work with ssl and I've got this one in error.log:

```
[Thu Jun 03 10:00:39 2010] [notice] child pid 26013 exit signal Segmentation fault (11)
[Thu Jun 03 10:00:39 2010] [notice] child pid 26014 exit signal Segmentation fault (11)
```

+1 for this error.
I've tried to move curl to the end of php5-modules, by renaming curl.ini to the zzzz-curl.ini - no success.

Will debug this error if somebody explain me how to to it.

---

### Post by sgoranov on 2010-06-05
Hello,
I want to mention that this one occurs only on x64. On x32 it works perfect. I installed Ubuntu x32 to test it.

---

### Post by karesmakro on 2010-06-05
This is not completly right. I had the same issue on a x86  plattform, but my issue was, as I was trying to load a vhost configuration used with ssl and not enabled the ssl module for apache2!
Never saw this behaviour on another distribution before!

**Edit** sorry, I did not read the full post

---

### Post by doudenit on 2010-06-07
I've filed a bug about this.
[https://bugs.launchpad.net/ubuntu/+source/apache2/+bug/590639](https://bugs.launchpad.net/ubuntu/+source/apache2/+bug/590639)

---

### Post by rizay on 2010-06-17
I have the same problem on 10.04 and, like the person before, it seems to be happening only on the 64-bit version and not the 32-bit version.  On a 64-bit installation on a production server I'm currently working on, I tried adding and removing the php5 extensions one at a time and was able to narrow it down to php5-curl.

I have a personal 32-bit machine at home and have been able to confirm that the same doesn't happen on that machine.

Like the person above, once I install that extension on the 64-bit machine, my browser indicates a server error whenever I try to access anything via HTTPS and a segmentation fault shows up in the Apache error logs.

Anyone know of a work-around?

---

### Post by grossvogel on 2010-07-03
i'm getting seg faults whenever i try to start apache with an SSL site enabled. I tried un-installing php5-curl, and it didn't change anything... anybody know how to fix this?

also 10.04, x64

---

### Post by khatkarrohit on 2010-09-17
I have the same problem.
I need php5-curl to run glype proxy. But after installing php5-curl SSL stops working. and if un-install php5-curl SSL start working fine but glype proxy stops working. I m using Ubuntu 10.04 with apache.

Error message from google chrome:

Error 107 (net::ERR_SSL_PROTOCOL_ERROR): SSL protocol error.

and apache error log:

[Fri Sep 17 15:56:01 2010] [notice] child pid 6552 exit signal Segmentation fault (11)

---

