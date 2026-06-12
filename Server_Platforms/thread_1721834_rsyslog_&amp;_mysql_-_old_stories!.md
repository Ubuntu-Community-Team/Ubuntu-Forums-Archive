---
title: "rsyslog &amp; mysql - old stories!"
date: 2011-04-05
forum: Server Platforms
---

### Post by 11notes on 2011-04-05
I try to log all my iptable logs to mysql instead just a logfile. The setup is as followed:

**mysql**
db: fw
user: rsyslog - all priv on db fw
table: drop - 2 fields - ID, MSG

**rsyslog**
$template fwdrop,"INSERT INTO `fw`.`drop` (`msg`) VALUES ('%msg%')",SQL
*.* :ommysql:localhost,fw,rsyslog,******;fwdrop

**[red]Problem[/red]**
rsyslog logs everything correct, except it does not log to db, it logs to /var/log/messages. As I am brand new to the whole Linux experience, I don't get it. My /etc/rsyslog.conf is setup with **$ModLoad onmysql**.

Has anybody an idea why it won't log to mysql?

---

### Post by 11notes on 2011-04-06
Fix'd it myself, solution:


1. forgot: apt-get install rsyslog-mysql
2. changed template to:
```

$ModLoad ommysql
$template fw,"INSERT INTO `fw`.`log` (`dt`, `src`, `dst`, `srcp`, `dstp`, `typ`) VALUES ('%timereported:::date-mysql%', '%msg:R,ERE,1,DFLT:SRC=([0-9]+\.[0-9]+\.[0-9]+\.[0-9]+)--end%', '%msg:R,ERE,1,DFLT:DST=([0-9]+\.[0-9]+\.[0-9]+\.[0-9]+)--end%', '%msg:R,ERE,1,DFLT:SPT=([0-9]+)--end%', '%msg:R,ERE,1,DFLT:DPT=([0-9]+)--end%', '%msg:R,ERE,1,DFLT:FIREWALL ([A-Z]+):--end%')",SQL
:msg,contains,"FIREWALL" :ommysql:localhost,fw,rsyslog,*********;fw

```

---

