---
title: "Apache2 in chroot shutdown at 6:45am most days"
date: 2009-03-01
forum: Server Platforms
---

### Post by ozman30 on 2009-03-01
Ubuntu 8.0.4.2 Base No GUI only CLI
Installed as followes
apt-get install \
apache2 \
libapache2-mod-chroot \
php5 \
php5-gd \
php5-mcrypt \
php5-mysql \
mysql-server \
mysql-client \
zip \
unzip \
php-pear

at 6:45 most days apache will shutsdown i modified the logrotation for apache to stop befor log rotation and to start after because when apache is in jail HUP will kill apache.

There is no log referance except for apaches caught SIGWINCH, shutting down gracefully and syslog test -x /usr/sbin/anacron
are the only things at that time

The fix for now is to run a second cron job to verify apache is running

What am i missing to fix this the proper way

---

