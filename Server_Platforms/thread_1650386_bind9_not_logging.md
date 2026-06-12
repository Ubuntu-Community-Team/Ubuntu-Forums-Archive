---
title: "bind9 not logging"
date: 2010-12-21
forum: Server Platforms
---

### Post by ddaas on 2010-12-21
Hi there,
I'am running Ubuntu server 10.10.
Bind instalation is the default one (apt-get install bind9).
It doesn't log the a file only to syslog. 
I need some help, I can't figure the problem.

In named.conf.options

     ```
ogging { 
        channel my_log { 
                file "/var/log/bind.log" versions 10 size 5M; 
                severity info;
                print-time yes;
                print-category yes;
                print-severity yes; 
        }; 

category queries { my_log; };  
        category default { my_log; };  
}; 

```
        
The file /var/log/bind.log exists and belongs to bind.

rndc status

```

version: 9.7.1-P2
CPUs found: 2
worker threads: 2
number of zones: 33
debug level: 0
xfers running: 0
xfers deferred: 0
soa queries in progress: 0
query logging is ON
recursive clients: 0/0/1000
tcp clients: 0/100
server is up and running 
```
     
     ls -l /var/log/bind.log 

```
 -rw-r----- 1 bind bind 1 2010-12-21 15:31 /var/log/bind.log 
```ps -ef  | grep named
```
bind      2723     1  0 15:58 ?        00:00:00 /usr/sbin/named -u bind
root      3502  3454  0 17:50 pts/0    00:00:00 grep --color=auto named
```

---

### Post by ddaas on 2010-12-21
Here is the solution. [https://lists.isc.org/pipermail/bind-users/2010-January/078473.html](https://lists.isc.org/pipermail/bind-users/2010-January/078473.html)

---

### Post by spezticle on 2012-10-25
> **ddaas said:**
> Here is the solution. [https://lists.isc.org/pipermail/bind-users/2010-January/078473.html](https://lists.isc.org/pipermail/bind-users/2010-January/078473.html)

dead link

---

### Post by nothingspecial on 2012-10-25
> **spezticle said:**
> dead link

Not surprising considering the age of the thread.

Closed.

---

### Post by mörgæs on 2012-10-25
From 10.10 to today it's likely that quite a bit has changed in Bind, and the information here might be obsolete. 

Closing the thread.

---

