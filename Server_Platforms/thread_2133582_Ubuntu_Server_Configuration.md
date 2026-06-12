---
title: "Ubuntu Server Configuration"
date: 2013-04-08
forum: Server Platforms
---

### Post by AndrejsLi on 2013-04-08
Hello!

I know almost nothing about the servers configuration, so I'm experiencing some problems with my new VPS.

1. Often homepage switches from normal working regime to this index: [https://lh4.googleusercontent.com/-Jv72uj1eqGQ/UWMMezHj2MI/AAAAAAAADJg/b9g-6h5D2Zg/s901/down.png](https://lh4.googleusercontent.com/-Jv72uj1eqGQ/UWMMezHj2MI/AAAAAAAADJg/b9g-6h5D2Zg/s901/down.png)
2. When the first problem is active, also it's not possible to make connection to server via remote control applications such as Putty, WinSCP;

Could this be an Apache2 configuration problem?

Temporary the problem disappears after restarting server.

Ubuntu version: 12. 04

Thanks

---

### Post by Habitual on 2013-04-08
Restarting apache would be my first choice.
It is almost never necessary, (or should never be) to reboot a server for One service-related issue.
What do the /var/logs say?

---

### Post by AndrejsLi on 2013-04-08
It's not possible to restart Apache because the control via remote is down too. I don't understand information in log files, and there are so much files..

---

### Post by AndrejsLi on 2013-04-09
Seriously, I'm a newbie and I want to find the problem solution. It's hard to work with system.

---

### Post by CharlesA on 2013-04-09
> **AndrejsLi said:**
> Seriously, I'm a newbie and I want to find the problem solution. It's hard to work with system.

Do you have access to the server's console? If you cannot connect to it remotely when this occurs, something is definitely wrong.

Check the apache error log to start and syslog might be helpful too.

```
tail /var/log/apache2/error.log
```

```
tail /var/log/syslog
```

---

### Post by AndrejsLi on 2013-04-10
[B]CharlesA,
[/B]
yes, it's not possible to connect remotely and websites are also down, although the domain pinging is successful.
[COLOR=#000000]
**veebrij**[/COLOR],

Sorry for this, but in Ubuntu help forum I'm searching for problem solving, not server configuration guide. But of course, your idea is good ;)

Part of log information:

Syslog file

Apr 10 08:47:14 andrejs xinetd[344]: Exiting...
Apr 10 08:47:18 andrejs named[472]: received control channel command 'stop -p'
Apr 10 08:47:18 andrejs named[472]: shutting down: flushing changes
Apr 10 08:47:18 andrejs named[472]: stopping command channel on 127.0.0.1#953
Apr 10 08:47:18 andrejs named[472]: stopping command channel on ::1#953
Apr 10 08:47:18 andrejs named[472]: no longer listening on ::#53
Apr 10 08:47:18 andrejs named[472]: no longer listening on 127.0.0.1#53
Apr 10 08:47:18 andrejs named[472]: no longer listening on 127.0.0.2#53
Apr 10 08:47:18 andrejs named[472]: no longer listening on 5.199.164.71#53
Apr 10 08:47:18 andrejs named[472]: exiting

Apache2 error

[Wed Apr 10 08:47:16 2013] [notice] caught SIGTERM, shutting down
[Wed Apr 10 08:47:27 2013] [notice] Apache/2.2.22 (Ubuntu) PHP/5.4.6-1ubuntu1.2 configured -- resuming normal operations

---

### Post by CharlesA on 2013-04-10
Check more of the syslog

How much memory is in use when this occurs?

---

### Post by AndrejsLi on 2013-04-10
The system doesn't has the RAM usage monitoring. And it's not possible to check it in this moments. Maybe it happens due some turning on / off or timeouts settings?

This is the last in syslog:

Apr 10 08:47:19 andrejs exiting on signal 15
Apr 10 08:47:23 andrejs syslogd 1.5.0#6ubuntu1: restart.
Apr 10 08:47:24 andrejs named[483]: starting BIND 9.8.1-P1 -u bind
Apr 10 08:47:24 andrejs named[483]: built with '--prefix=/usr' '--mandir=/usr/share/man' '--infodir=/usr/share/info' '--sysconfdir=/etc/bind' '--localstatedir=/var' '--enable-threads' '--enable-largefile' '--with-libtool' '--enable-shared' '--enable-static' '--with-openssl=/usr' '--with-gssapi=/usr' '--with-gnu-ld' '--with-geoip=/usr' '--enable-ipv6' 'CFLAGS=-fno-strict-aliasing -DDIG_SIGCHASE -O2'
Apr 10 08:47:24 andrejs named[483]: adjusted limit on open files from 4096 to 1048576
Apr 10 08:47:24 andrejs named[483]: found 1 CPU, using 1 worker thread
Apr 10 08:47:24 andrejs named[483]: using up to 4096 sockets
Apr 10 08:47:24 andrejs named[483]: loading configuration from '/etc/bind/named.conf'
Apr 10 08:47:24 andrejs named[483]: reading built-in trusted keys from file '/etc/bind/bind.keys'
Apr 10 08:47:24 andrejs named[483]: using default UDP/IPv4 port range: [1024, 65535]
Apr 10 08:47:24 andrejs named[483]: using default UDP/IPv6 port range: [1024, 65535]
Apr 10 08:47:24 andrejs named[483]: listening on IPv6 interfaces, port 53
Apr 10 08:47:24 andrejs named[483]: listening on IPv4 interface lo, 127.0.0.1#53
Apr 10 08:47:24 andrejs named[483]: listening on IPv4 interface venet0, 127.0.0.2#53
Apr 10 08:47:24 andrejs named[483]: listening on IPv4 interface venet0:0, 5.199.164.71#53
Apr 10 08:47:24 andrejs named[483]: generating session key for dynamic DNS
Apr 10 08:47:24 andrejs named[483]: sizing zone task pool based on 5 zones
Apr 10 08:47:24 andrejs named[483]: using built-in root key for view _default
Apr 10 08:47:24 andrejs named[483]: set up managed keys zone for view _default, file 'managed-keys.bind'
Apr 10 08:47:24 andrejs named[483]: Warning: 'empty-zones-enable/disable-empty-zone' not set: disabling RFC 1918 empty zones
Apr 10 08:47:24 andrejs named[483]: automatic empty zone: 254.169.IN-ADDR.ARPA
Apr 10 08:47:24 andrejs named[483]: automatic empty zone: 2.0.192.IN-ADDR.ARPA
Apr 10 08:47:24 andrejs named[483]: automatic empty zone: 100.51.198.IN-ADDR.ARPA
Apr 10 08:47:24 andrejs named[483]: automatic empty zone: 113.0.203.IN-ADDR.ARPA
Apr 10 08:47:24 andrejs named[483]: automatic empty zone: 255.255.255.255.IN-ADDR.ARPA
Apr 10 08:47:24 andrejs named[483]: automatic empty zone: 0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.IP6.ARPA
Apr 10 08:47:24 andrejs named[483]: automatic empty zone: 1.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.IP6.ARPA
Apr 10 08:47:24 andrejs named[483]: automatic empty zone: D.F.IP6.ARPA
Apr 10 08:47:24 andrejs named[483]: automatic empty zone: 8.E.F.IP6.ARPA
Apr 10 08:47:24 andrejs named[483]: automatic empty zone: 9.E.F.IP6.ARPA
Apr 10 08:47:24 andrejs named[483]: automatic empty zone: A.E.F.IP6.ARPA
Apr 10 08:47:24 andrejs named[483]: automatic empty zone: B.E.F.IP6.ARPA
Apr 10 08:47:24 andrejs named[483]: automatic empty zone: 8.B.D.0.1.0.0.2.IP6.ARPA
Apr 10 08:47:24 andrejs named[483]: command channel listening on 127.0.0.1#953
Apr 10 08:47:24 andrejs named[483]: command channel listening on ::1#953
Apr 10 08:47:24 andrejs named[483]: zone 0.in-addr.arpa/IN: loaded serial 1
Apr 10 08:47:24 andrejs named[483]: zone 127.in-addr.arpa/IN: loaded serial 1
Apr 10 08:47:24 andrejs named[483]: zone 255.in-addr.arpa/IN: loaded serial 1
Apr 10 08:47:24 andrejs named[483]: zone localhost/IN: loaded serial 2
Apr 10 08:47:24 andrejs named[483]: managed-keys-zone ./IN: loaded serial 3
Apr 10 08:47:24 andrejs named[483]: running
Apr 10 08:47:24 andrejs sm-mta[590]: gethostbyaddr(127.0.0.2) failed: 1
Apr 10 08:47:24 andrejs sm-mta[592]: starting daemon (8.14.4): SMTP+queueing@00:10:00
Apr 10 08:47:25 andrejs sm-mta[593]: r39G922P001173: to=<v**e@inbox.lv>, ctladdr=<www-data@andrejs.domain.lt> (33/33), delay=20:38:23, xdelay=00:00:00, mailer=esmtp, pri=11550899, relay=b.mx.inbox.lv. [89.111.3.74], dsn=4.1.8, stat=Deferred: 450 4.1.8 <www-data@andrejs.domain.lt>: Sender address rejected: Domain not found
Apr 10 08:47:25 andrejs sm-mta[593]: r39G922P001173: to=<v**e@inbox.lv>, ctladdr=<www-data@andrejs.domain.lt> (33/33), delay=20:38:23, xdelay=00:00:00, mailer=esmtp, pri=11550899, relay=a.mx.inbox.lv. [89.111.3.72], dsn=4.1.8, stat=Deferred: 450 4.1.8 <www-data@andrejs.domain.lt>: Sender address rejected: Domain not found
Apr 10 08:47:25 andrejs sm-mta[593]: r39G6bIQ001151: to=<vi**e@inbox.lv>, ctladdr=<www-data@andrejs.domain.lt> (33/33), delay=20:40:48, xdelay=00:00:00, mailer=esmtp, pri=11640934, relay=b.mx.inbox.lv. [89.111.3.74], dsn=4.1.8, stat=Deferred: 450 4.1.8 <www-data@andrejs.domain.lt>: Sender address rejected: Domain not found
Apr 10 08:47:25 andrejs sm-mta[593]: r39G6bIQ001151: to=<v**e@inbox.lv>, ctladdr=<www-data@andrejs.domain.lt> (33/33), delay=20:40:48, xdelay=00:00:00, mailer=esmtp, pri=11640934, relay=a.mx.inbox.lv. [89.111.3.72], dsn=4.1.8, stat=Deferred: 450 4.1.8 <www-data@andrejs.domain.lt>: Sender address rejected: Domain not found
Apr 10 08:47:25 andrejs sm-mta[593]: r39G7DvB001156: to=<v**e@inbox.lv>, ctladdr=<www-data@andrejs.domain.lt> (33/33), delay=20:40:12, xdelay=00:00:00, mailer=esmtp, pri=11640934, relay=b.mx.inbox.lv. [89.111.3.74], dsn=4.1.8, stat=Deferred: 450 4.1.8 <www-data@andrejs.domain.lt>: Sender address rejected: Domain not found
Apr 10 08:47:25 andrejs sm-mta[593]: r39G7DvB001156: to=<v**e@inbox.lv>, ctladdr=<www-data@andrejs.domain.lt> (33/33), delay=20:40:12, xdelay=00:00:00, mailer=esmtp, pri=11640934, relay=a.mx.inbox.lv. [89.111.3.72], dsn=4.1.8, stat=Deferred: 450 4.1.8 <www-data@andrejs.domain.lt>: Sender address rejected: Domain not found
Apr 10 08:47:25 andrejs /etc/mysql/debian-start[601]: Upgrading MySQL tables if necessary.
Apr 10 08:47:25 andrejs /etc/mysql/debian-start[604]: /usr/bin/mysql_upgrade: the '--basedir' option is always ignored
Apr 10 08:47:25 andrejs /etc/mysql/debian-start[604]: Looking for 'mysql' as: /usr/bin/mysql
Apr 10 08:47:25 andrejs /etc/mysql/debian-start[604]: Looking for 'mysqlcheck' as: /usr/bin/mysqlcheck
Apr 10 08:47:25 andrejs /etc/mysql/debian-start[604]: This installation of MySQL is already upgraded to 5.5.29, use --force if you still need to run mysql_upgrade
Apr 10 08:47:25 andrejs /etc/mysql/debian-start[615]: Checking for insecure root accounts.
Apr 10 08:47:25 andrejs /etc/mysql/debian-start[620]: Triggering myisam-recover for all MyISAM tables

Temporary wasn't configured right sites-enabled settings, so maybe there are also this errors.

---

### Post by SeijiSensei on 2013-04-10
Some VPS providers like Linode offer the option to run a console on the machine over the web.  If that's available to you, you'll be able to work with the machine even if you cannot connect to it with SSH.

---

### Post by CharlesA on 2013-04-10
> **SeijiSensei said:**
> Some VPS providers like Linode offer the option to run a console on the machine over the web.  If that's available to you, you'll be able to work with the machine even if you cannot connect to it with SSH.

My VPS provider support that serial console thing too. I haven't had to use it yet, but it's nice to know it's an option.

@ AndrejsLi: The log looks ok to me, but if you can get console access to the machine when it locks up, it would be a start.

---

### Post by AndrejsLi on 2013-04-11
Thank you all.

This wasn't the server configuration problem, but network. Hosting provider doesn't noticed it.

---

