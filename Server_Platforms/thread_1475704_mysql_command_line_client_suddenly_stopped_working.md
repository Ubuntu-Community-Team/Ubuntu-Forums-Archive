---
title: "mysql command line client suddenly stopped working"
date: 2010-05-07
forum: Server Platforms
---

### Post by mvb_marksman on 2010-05-07
Hi,

I have been using the mysql command line client a lot before but it suddenly stopped working.

The error message is:

> mysql: relocation error: mysql: symbol strmov_overlapp, version libmysqlclient_16 not defined in file libmysqlclient.so.16 with link time reference

The only significant event that comes into mind is updating from Ubuntu 9.10 to 10.4.  I'm not sure if there's anything else that I did to mess it up.

I tried uninstalling both the mysql server and mysql client like so but to no avail.

```
sudo aptitude purge mysql-server-5.1
```

Any help will be much appreciated, thanks.

---

### Post by terazen on 2010-05-07
I don't think that I've ever seen that particular error, but I have had a similar error that running ldconfig fixed.  Free bump if nothing else. :-)

---

### Post by mrfelton on 2010-05-08
Same problem for me. Since upgrading to 10.04

---

### Post by crowdofone on 2010-10-01
I'm having the same issue on my server (CentOS 5.4) and found that: ```
rpm -e --nodeps mysql-libs
``` allowed me to access mysql on the command line again.

---

