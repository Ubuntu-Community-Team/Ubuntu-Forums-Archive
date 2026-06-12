---
title: "MySQL Refusing Connections from Localhost"
date: 2012-10-07
forum: Server Platforms
---

### Post by mootpoint on 2012-10-07
My mail server (Ubuntu 10.04) uses mysql for virtual domains, virtual users. For some reason, mysqld has started refusing connections from localhost. I see these in the mail server log:

Oct 6 00:31:14 apollo postfix/trivial-rewrite[16888]: fatal: proxy:mysql:/etc/postfix/mysql-virtual_domains.cf(0,lock|fold_fix): table lookup problem

and:

Oct 7 13:39:15 apollo postfix/proxymap[25839]: warning: connect to mysql server 127.0.0.1: Lost connection to MySQL server at 'reading initial communication packet', system error: 0


I also get the following in auth.log:
Oct 6 22:33:31 apollo mysqld[31775]: refused connect from 127.0.0.1

Telnet to the local port:

root@apollo:/var/log/mysql# telnet localhost 3306
Trying ::1...
Trying 127.0.0.1...
Connected to localhost.
Escape character is '^]'.
Connection closed by foreign host.
root@apollo:/var/log/mysql#

I am not sure why this started happening, but there was a disk failure in a RAID 1 pair a bit earlier that day. So it's possible I have a damaged config file or something. But mail was working for at least an hour after the drive event, so who knows for sure?

phpmyadmin works fine, and the databases themselves look like they're intact.

I think/believe that selinux and iptables are disabled and not running. So ... why is mysqld refusing connections from localhost? What should I check? What processes might cause this if a .conf file or possibly a binary was damaged? Which other log files might contain clues? I've enabled "general logging" in /etc/mysql/my.cnf, but I get no interesting or informative entries there.

Thanks,
m00t

---

