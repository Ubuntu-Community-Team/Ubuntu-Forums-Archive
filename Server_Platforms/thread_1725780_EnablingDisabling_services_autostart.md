---
title: "Enabling/Disabling services autostart"
date: 2011-04-10
forum: Server Platforms
---

### Post by Ghost_Mazal on 2011-04-10
Lo All ,

How do you enable/disable the autostart of services. For example let's say I know I'm not gonna use apache and mysql for a while and don't want it to autostart anymore how do I disable it ?

And then once it is needed again how do you enable the autostart again ?

Thanx

---

### Post by CharlesA on 2011-04-10
I'd just remove the execute permission from the file /etc/init.d, but there are easier ways to do it.

Like this [one]("http://www.debian-administration.org/articles/28").

---

### Post by BkkBonanza on 2011-04-10
I usually use,

sudo update-rc.d <appname> disable

but I've read this is frowned on now. For newer configs using Upstart I usually just rename the conf file eg.

sudo mv /etc/init/<appname>.conf /etc/init/<appname>.conf.disabled

since it only acts on the ones ending with .conf. 

Some services have a enable/disable option in a file in /etc/defaults/<appname>

It would be nice if someday they finally get them all caught up to a standard.

---

### Post by SeijiSensei on 2011-04-10
This situation where some daemons use upstart and others use the older /etc/init.d system is really a pain.  I've seen a number of requests like the OP's about enabling or disabling services, and unless you've used a particular program, you now simply have no idea which init method it uses.  Upstart may be a fine idea, but it should never have been introduced piecemeal.  The packagers should have left everything under the old system until there were working upstart modules for every program that comes by default with Ubuntu Server and probably even a few, like OpenVPN, that don't.

That's one reason why I don't use Ubuntu Server on production deployments.  "chkconfig" and "service" work consistently for all server daemons in RHEL/CentOS.

---

### Post by Ghost_Mazal on 2011-04-10
Seems like this is a tricky one. I checked out my /etc/init and some servers (like samba for ex) doesn't even have a .conf file there.

---

### Post by CharlesA on 2011-04-10
> **BkkBonanza said:**
> I usually use,

sudo update-rc.d <appname> disable

but I've read this is frowned on now. For newer configs using Upstart I usually just rename the conf file eg.

sudo mv /etc/init/<appname>.conf /etc/init/<appname>.conf.disabled

since it only acts on the ones ending with .conf. 

Some services have a enable/disable option in a file in /etc/defaults/<appname>

It would be nice if someday they finally get them all caught up to a standard.

I checked /etc/init.d on my lucid server box and didn't see any *.conf files in /etc/init.d.

Some were symlinks to /lib/init/upstart-job

---

