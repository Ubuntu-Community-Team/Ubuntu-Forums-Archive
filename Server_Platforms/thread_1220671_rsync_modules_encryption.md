---
title: "rsync modules encryption"
date: 2009-07-23
forum: Server Platforms
---

### Post by tall-male on 2009-07-23
I like the rsync-server, that is: rsync in daemon mode since it can be configured (/etc/rsyncd.conf) using modules like:

[INDENT]motd file = /etc/rsyncd.motd
log file = /var/log/rsyncd.log
pid file = /var/run/rsyncd.pid
lock file = /var/run/rsync.lock
syslog facility = daemon

[apache-content]
   use chroot = no
   auth users = apache-manager
   path = /var/www/html
   comment = Apache html content
   uid = nobody
   gid = nobody
   read only = yes
   list = yes
   secrets file = /etc/rsyncd.secrets
   ignore nonreadable = yes[/INDENT]

However, using it in this manner, transfer is done _without encryption_. Yes, one can use ssh (rsync -vaz -e ssh ....) but using ssh I cannot access the rsync-server by modules:

rsync -vaz apache-manager@<host>::apache <local dir> is OK
rsync -vaz -e "/usr/bin/ssh -l apache-manager" <host>:: is NOT OK since rsync & SSH cannot be used with the modules. Too bad, since I want encryption while transfering the files, and no, I do not want to use the full path like:

rsync -vaz -e "/usr/bin/ssh -l apache-manager" <host>:/var/www/html <local dir>
` 
Searching Google showed me that using rsync modules and ssh is not possible.
Did I miss something, and is it possible? Is there another way to encrypt rsync data communication? The only workaround so far seems things like stunnel, but is the native SSL-support for rsync?

Thankz!

---

