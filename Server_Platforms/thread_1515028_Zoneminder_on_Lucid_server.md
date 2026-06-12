---
title: "Zoneminder on Lucid server"
date: 2010-06-21
forum: Server Platforms
---

### Post by Leppie on 2010-06-21
i've installed zoneminder on lucid server from the repos, but it doesn't start.
it gives me a the following simple error:
```
Starting ZoneMinder: failure
```and the syslog only says:
```
Jun 22 01:21:39 hfmain zmpkg[4391]: INF [Command: start]
```dmesg doesn't seem to report anything regarding this, the entries after trying to start zoneminder look like this (looks like a cups error to me):
```
type=1503 audit(1277156481.110:32):  operation="open" pid=1584 parent=1 profile="/usr/sbin/cupsd" requested_mask="r::" denied_mask="r::" fsuid=0 ouid=0 name="/var/run/samba/gencache.tdb"
```any help greatly appreciated :)

---

### Post by bertmanphx on 2010-06-22
Leppie,
When you installed it, you should have been prompted to enter some information for mysql and such.  If that did not occur, you may want to re-install the software.

bertmanphx

---

### Post by Leppie on 2010-06-22
the funny thing is, it didn't prompt me at all for anything during installation. there were only the normal apt messages.
i checked mysql, but zoneminder had created a database and tables and all. though i don't know how as i don't have a root account in mysql...

will try to purge and re-install.

---

### Post by Leppie on 2010-06-23
so i re-installed it, but there's no zoneminder folder in /var/www/
there's a zm archive, which apparently is cambozola.

any suggestions?

---

### Post by Leppie on 2010-06-23
ok, so i found the zoneminder files in /usr/share/zoneminder rather than in /var/www/

---

### Post by maufacc on 2010-07-20
just to complete your auto-answer.
After install the package you should 
 sudo ln -s /etc/zm/apache.conf /etc/apache2/conf.d/zoneminder.conf, 
Then you can access zm with [http://your.server.ip/zm](http://your.server.ip/zm)

---

