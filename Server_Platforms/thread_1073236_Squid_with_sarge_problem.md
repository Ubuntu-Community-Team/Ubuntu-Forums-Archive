---
title: "Squid with sarge problem"
date: 2009-02-18
forum: Server Platforms
---

### Post by StarF on 2009-02-18
Hi

I am setting up a squid with ubuntu, and i have addet the sarg module, so i can generate reports. I am using webmin to do the general config of these things.

i have setup up sarg to use sendmail to send my report, and i have addet the mail i want it to send to, in its config file with webmin (the sarg config file)

when i try to generate a report i am getting this output:

```
sarg -l /var/log/squid/access.log 
SARG: Loading exclude file from: /etc/squid/sarg.hosts
SARG: Loading exclude file from: /etc/squid/sarg.users
SARG: Parameters:
SARG:
SARG:              Hostname or IP address (-a) = 
SARG:                       Useragent log (-b) = 
SARG:                        Exclude file (-c) = /etc/squid/sarg.hosts
SARG:                     Date from-until (-d) = 
SARG:       Email address to send reports (-e) = mhs@mariendal.dk
SARG:                         Config file (-f) = /etc/squid/sarg.conf
SARG:                         Date format (-g) = USA (mm/dd/yyyy)
SARG:                           IP report (-i) = No
SARG:                           Input log (-l) = /var/log/squid/access.log
SARG:                  Resolve IP Address (-n) = No
SARG:                          Output dir (-o) = /tmp/sarg/
SARG:    Use Ip Address instead of userid (-p) = No
SARG:                       Accessed site (-s) = 
SARG:                                Time (-t) = 
SARG:                                User (-u) = 
SARG:                       Temporary dir (-w) = /tmp
SARG:                      Debug messages (-x) = Yes
SARG:                    Process messages (-z) = No
SARG:
SARG: sarg version: 2.2.5 Mar-03-2008
SARG: Maximum file descriptor: cur=1024 max=1024, changed to cur=20000 max=20000
SARG: Loading User table: /etc/squid/sarg.usertab
SARG: Reading access log file: /var/log/squid/access.log
SARG:    Records read: 103, written: 102, excluded: 1
SARG: Squid log format
SARG: Period: 2009Feb18-2009Feb18
SARG: pre-sorting files
SARG: Making period file
SARG: Making file: /tmp/sarg/10.1.1.167
SARG: Sorting file: /tmp/sarg/10.1.1.167
sendmail: RCPT TO:<SARG Report@me.local.com> (501 Bad address syntax)
SARG: End

```

i cant find anywhere there the mail [email]report@me.local.com[/email] has ben set. can any one help with this?

---

