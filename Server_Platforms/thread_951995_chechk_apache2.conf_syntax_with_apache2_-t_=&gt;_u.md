---
title: "chechk apache2.conf syntax with apache2 -t =&gt; user error"
date: 2008-10-18
forum: Server Platforms
---

### Post by mansonthomas on 2008-10-18
Hi,

I'm trying to make a syntax check of my apache2.conf.

root@home:/etc/apache2/sites-available# sudo -u www-data apache2 -t
apache2: bad user name ${APACHE_RUN_USER}


thomas@home:/home/special/www$ cat /etc/apache2/envvars
# envvars - default environment variables for apache2ctl


apache2.conf excerpt : 

[PHP]# These need to be set in /etc/apache2/envvars
User ${APACHE_RUN_USER}
Group ${APACHE_RUN_GROUP}[/PHP]

[PHP]
thomas@home:/home/special/www$ cat /etc/apache2/envvars
# Since there is no sane way to get the parsed apache2 config in scripts, some
# settings are defined via environment variables and then used in apache2ctl,
# /etc/init.d/apache2, /etc/logrotate.d/apache2, etc.
export APACHE_RUN_USER=www-data
export APACHE_RUN_GROUP=www-data
export APACHE_PID_FILE=/var/run/apache2.pid[/PHP]

Even if I su - www-data, it can't run...

So how do I check my configuration file ? (unless modifying User & Group in apache.conf)

Thomas

---

