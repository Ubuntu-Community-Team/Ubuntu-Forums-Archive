---
title: "start apache on nonstandard port"
date: 2011-08-30
forum: Server Platforms
---

### Post by bluethundr on 2011-08-30
hello,

 I'm trying to setup a statusnet server on an existing ubuntu based
zimbra server. Zimbra uses it's own brand of apache and I installed a
separate apache2 to manage the status net install.

Server info
```

root@li289-212:/var/www# cat /etc/issue
Ubuntu 10.04 LTS \n \l

root@li289-212:/var/www# uname -a
Linux li289-212 2.6.39.1-x86_64-linode19 #1 SMP Tue Jun 21 10:04:20
EDT 2011 x86_64 GNU/Linux

```

Apache info
```


root@li289-212:/var/www# dpkg -l | grep apache
ii  apache2                         2.2.14-5ubuntu8.4           Apache
HTTP Server metapackage
ii  apache2-mpm-worker              2.2.14-5ubuntu8.4           Apache
HTTP Server - high speed threaded mod
ii  apache2-utils                   2.2.14-5ubuntu8.4
utility programs for webservers
ii  apache2.2-bin                   2.2.14-5ubuntu8.4           Apache
HTTP Server common binary files
ii  apache2.2-common                2.2.14-5ubuntu8.4           Apache
HTTP Server common files
ii  zimbra-apache                   7.1.0_GA_3140.UBUNTU10_64   Best
email money can buy

```


 However when I try to start apache on the alternate port it claims
that the port is already in use although I'm stumped as to why using
the standard tools.

Apache set to listen on alternate port
```

root@li289-212:/var/www# grep -ri listen /etc/apache2/
/etc/apache2/ports.conf:Listen 10000
/etc/apache2/ports.conf:    Listen 443
/etc/apache2/ports.conf:    Listen 443
/etc/apache2/apache2.conf:Listen 10000

```


apache fails to start
```

root@li289-212:/var/www# /etc/init.d/apache2 start
 * Starting web server apache2
        (98)Address already in use: make_sock: could not bind to
address 0.0.0.0:10000
no listening sockets available, shutting down
Unable to open logs
                                                                        [fail]

```

Looking for what could be listening on that non-standard port
```

root@li289-212:/var/www# netstat -tulpn | grep 10000
root@li289-212:/var/www# netstat -tapn | grep 10000
root@li289-212:/var/www# lsof -i :10000

```



:???:


Can anyone provide a hint as to how best to troubleshoot this scenario?

Thanks!
Tim

---

### Post by sergio-bobillier on 2011-08-31
Well I was checking my Apache 2 settings and found this:

```
# If you just change the port or add more ports here, you will likely also
# have to change the VirtualHost statement in
# /etc/apache2/sites-enabled/000-default
# This is also true if you have upgraded from before 2.2.9-3 (i.e. from
# Debian etch). See /usr/share/doc/apache2.2-common/NEWS.Debian.gz and
# README.Debian.gz
```

This lines are from the ports.conf file So I wonder did you check your Virtual Host File?

---

