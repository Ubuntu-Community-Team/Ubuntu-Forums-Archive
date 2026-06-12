---
title: "denied permissions for rndc.key and session.key (BIND 9.8.1-P1 -g)"
date: 2013-11-06
forum: Server Platforms
---

### Post by clearski on 2013-11-06
Hi.

Could anybody please post the file permissions for:

/var/run/named/named.pid
/var/run/named/session.key ?

I get these two errors:

```
could not open file '/var/run/named/named.pid': Permission denied
could not open file '/var/run/named/session.key': Permission denied
```

My permissions are 644 (bind:bind) for named.pid and 600 (bind:bind) for session.key

The DNS server is running fine and does its job, only that I am getting these errors at startup.

Thank you!

---

### Post by clearski on 2013-11-07
It seems that there are no real problems or errors with the permissions. That is great, even if it took me a day to figure out, including  reinstalling bind.

named.pid and session.key are both created  upon starting bind9 and are removed when the service is stopped. So the  parent directory and the files within can be accessed whatsoever.

The  denied permissions above and some other warnings (" *could not listen on  UDP socket: permission denied* ") that are displayed with the command "**named -g**" are  actually generated because this command is run with a regular user privileges, whereas these files and this kind of information require higher privileges. So, running "**sudo named -g**" will show that everything is working just fine.

Solved.

---

