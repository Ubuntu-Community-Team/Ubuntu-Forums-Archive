---
title: "mod_rpaf not working after upgrade to 12.04"
date: 2012-05-23
forum: Server Platforms
---

### Post by parsim on 2012-05-23
Since upgrading my servers to Ubuntu Server 12.04, I've been unable to get the reverse proxy add forward module (rpaf, or mod_rpaf) to work.

We have a couple of servers sitting behind an Amazon.com Elastic Load Balancer, and usually all I need to do to extract the correct IP address is make sure the proxy's IP address is configured here:

```
$ more /etc/apache2/mods-available/rpaf.conf
<IfModule mod_rpaf.c>
RPAFenable On
RPAFsethostname On
RPAFproxy_ips 127.0.0.1 10.195.201.14 ::1
</IfModule>
```

Now, however, it's simply not working, and /var/log/apache2/access.log shows only the Load Balancer's IP, not the users'.

I've triple-checked that the module is actually installed and running, tried restarting the server, but nothing's having any effect.

---

### Post by parsim on 2012-05-25
Caused by [a Ubuntu bug](https://bugs.launchpad.net/ubuntu/+source/libapache2-mod-rpaf/+bug/1002571) (link contains workaround).

---

