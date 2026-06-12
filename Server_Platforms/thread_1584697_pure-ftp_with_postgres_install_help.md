---
title: "pure-ftp with postgres install help"
date: 2010-09-29
forum: Server Platforms
---

### Post by xkaliburx on 2010-09-29
Looking to run pure-ftp server with a postgres backend database which is already in use working.  I installed have the following installed;

p   mysqmail-pure-ftpd-logger       - real-time logging system in MySQL - Pure-F
p   pure-ftpd                       - Pure-FTPd FTP server                      
i A pure-ftpd-common                - Pure-FTPd FTP server (Common Files)       
p   pure-ftpd-ldap                  - Pure-FTPd FTP server with LDAP user authen
p   pure-ftpd-mysql                 - Pure-FTPd FTP server with MySQL user authe
i   pure-ftpd-postgresql            - Pure-FTPd FTP server with PostgreSQL user 

The 1st question is do I need to have pure-ftpd installed?  I would think if so, aptitude would take care of that, but now I can see the following in ps;

pgsql:/etc/pure-ftpd/db/postgresql.conf -l pam -u 1000 -O clf:/var/log/pure-ftpd/transfer.log -E -8 UTF-8 -o -B -g /var/run/pure-ftpd/pure-ftpd.pid
If you do an /etc/init.d/pure <tab> it autocompletes with; pure-ftp-postgres which you can start/stop, etc.   I did say start (which you can see from the PS), but if you try to connect you simply get a 'connection refused' .  And under /var/log/pure-ftp there is nothing and nothing in the messages file.

Anyone running pure with postgres, feel free to throw out .02 ... 
Thanks

---

