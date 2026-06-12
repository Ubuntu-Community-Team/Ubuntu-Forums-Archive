---
title: "apache2.conf missing from installation"
date: 2011-11-02
forum: Server Platforms
---

### Post by diob15 on 2011-11-02
Using: Ubuntu server 11.10
Problem: apache2.conf missing --also-- unable to find apache2 directory
Tried: Uninstalled, reinstalled apache2
Apache dependencies have been installed

Used:

# find / -name apache2

/etc/cron.daily/apache2
/etc/default/apache2
/etc/php5/apache2
/etc/logrotate.d/apache2
/etc/init.d/apache2
/var/lib/update-rc.d/apache2
/var/cache/apache2
/var/log/apache2
/usr/share/doc/apache2.2-common/examples/apache2
/usr/share/doc/apache2
/usr/share/apache2
/usr/share/bug/apache2
/usr/sbin/apache2
/usr/lib/apache2
/usr/lib/apache2/mpm-itk/apache2
/usr/lib/apache2/mpm-event/apache2
/usr/lib/apache2/mpm-worker/apache2
/usr/lib/apache2/mpm-prefork/apache2

I am unable to find the apache2 directory to open apache2.conf

Has anyone encountered this issue?

---

### Post by vasile002 on 2011-11-03
I believe you uninstalled apache and then manually removed the dir. Now when you install it dpkg thinks the apache2 dir exists already and it does not re-create/overwrite it.

Try purging the package and then install it again

---

### Post by diob15 on 2011-11-08
Issue solved. Thank you for you time.
[LEFT][COLOR=#333333][FONT=Ubuntu Beta]
To replace configuration files that have been deleted, without purging the package,[/FONT][/COLOR]

[COLOR=#333333][FONT=Ubuntu Beta]sudo apt-get -o DPkg::Options::="--force-confmiss" --reinstall install apache2.2-common [/FONT][/COLOR][/LEFT]

---

