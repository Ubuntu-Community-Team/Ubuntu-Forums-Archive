---
title: "OpenLDAP slapd: Too many open files"
date: 2007-11-20
forum: Server Platforms
---

### Post by fastkeys38 on 2007-11-20
Hi!

We're running two Samba servers as PDC and BDC that auth against OpenLDAP services running on the same pair of servers.

Both are running 6.06 Server LTS.

One of the servers, CORE02, has recently started refusing to answer LDAP queries for Samba (or any other LDAP client) and persistently logs the following in /var/log/syslog:

> Nov 19 10:23:03 core02 slapd[15476]: warning: cannot open /etc/hosts.allow: Too many open files

Issuing

> /etc/init.d/slapd restart

Solves the problem for about 24 hours before the problem recurrs.

Google finds lots of hits on this error. Thus far I've tried:

[LIST=1]
[*]Adding an idle timeout directive to the slapd.conf
[*]Using sysctrl increased the number of filehandles to 400,000
[/LIST]

The only other possible solutions I've come across refer to increasing the number of filehandles at compile time for the slapd daemon.

Does anyone have any further insight please?!

Thanks

Alex

---

### Post by honeydew on 2008-04-15
I have also encountered this issue.. so issueing a slapd restart only fixed it for 24 hours? err.. okay.. Ill have to watch this one closely.  how long had your ldap server been running?  ours has been running for 1.5 years and just ran into this issue.  I was hoping  /etc/init.d/slapd restart would let it run for another 1.5 years.

---

