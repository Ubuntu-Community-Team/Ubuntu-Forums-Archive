---
title: "System Log for remote machines"
date: 2009-05-10
forum: Server Platforms
---

### Post by pmla on 2009-05-10
Hi,

I'm running server 8.10 and of course have system logs deamon running.

My question is, can this deamon handle remote logging that is, receive the logs of my gateway?

The gateway does not have a lot of memory to store the logs but, I as the option to send the logs to a log server.
Gateway remote logging available options:
1. Name/IP: (log server Ip)
2. Port: 514 (can change port)
3. Minimum log level: Facility
4. Enable CSV Format: Y/N

Also running webmin, and can access system logs admin from there.

---

### Post by pmla on 2009-05-11
**** BUMP 1 off 3 ****

---

### Post by hw-tph on 2009-05-11
I have done remote logging using syslog-ng a couple of years ago. It wasn't too hard to set up. sysklogd, as found in stock Ubuntu, only seems to need a few changes to the config files as well.

Have a look at the sysklogd man page (**man 8 sysklogd**), and [this web page]("http://ubuntu-tutorials.com/2007/08/04/configure-local-and-remote-system-logging-ubuntu/") might prove some insight or tips as well.

---

