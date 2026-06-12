---
title: "Apache Problems"
date: 2009-04-12
forum: Server Platforms
---

### Post by Promaster91 on 2009-04-12
I am trying to setup a SVN server on my Ubuntu server. I installed all the stuff using XAMP. When I follow this tutorial [http://www.debian-resources.org/node/130](http://www.debian-resources.org/node/130) everthing goes well except for loading these two modules for SVN.
```

LoadModule dav_svn_module modules/mod_dav_svn.so
LoadModule authz_svn_module modules/mod_authz_svn.so

```


I get this error message when I try to restart Apache.
```

Starting XAMPP for Linux 1.6.8a...
XAMPP: Starting Apache with SSL (and PHP5)...
XAMPP: Error 139! Couldn't start Apache!
XAMPP: Starting diagnose...
XAMPP: Sorry, I've no idea what's going wrong.

```
I copied the modules to my /modules folder and I have confirmed that they are there. Does anybody know how to fix this. Thanks.

---

### Post by karlw on 2009-08-09
I'm not familiar with XAMPP, but you could post the end of you apache error log to see if anything helpful is posted there.  If I had to take a wild guess, I would wonder if the modules you copied have the same owners and permissions as the other modules in this directory.

Possible help:

[http://forum.eeeuser.com/viewtopic.php?id=16704](http://forum.eeeuser.com/viewtopic.php?id=16704)

---

