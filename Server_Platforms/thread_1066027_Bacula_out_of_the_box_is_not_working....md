---
title: "Bacula out of the box is not working..."
date: 2009-02-10
forum: Server Platforms
---

### Post by mansonthomas on 2009-02-10
Hi,


I've installed bacula (I'm a beginner on this bacula subject) on ubuntu server 8.10 with mysql as DBMS.

I've found that the password asked upon installation (bacula user for mysql) is not set in the /etc/bacula/bacula-dir.conf, catalog options, I've set it so that bacula can start.

All service start and keep running.

When I launch the bconsole utility, it succeed, but if I try to get the status of the current client (FD of the same machine) I get a timeout...

[PHP]*status client
Automatically selected Client: home.paquerette.com-fd
Connecting to Client home.paquerette.com-fd at home.paquerette.com:9102
Failed to connect to Client home.paquerette.com-fd.
====
You have messages.
*
10-Feb 20:33 home.paquerette.com-dir JobId 0: Fatal error: bsock.c:129 Unable to connect to Client: home.paquerette.com-fd on home.paquerette.com:9102. ERR=Connection timed out
*
[/PHP]

any idea ? 

Thomas

---

### Post by mansonthomas on 2009-02-10
btw, bacula version on ubuntu 8.10 is quite old (july 2008), is there anyway to get a newer version by adding some sources in /etc/apt/sources.list ? 

Thomas

---

### Post by Endwin on 2009-02-10
Did you check your config files and make sure the allowed addresses are correct for the machine? Specifically the  DirAddress field? Should include the public IP (not just 127.0.0.1) or just comment out the field for a home setup.

---

### Post by mansonthomas on 2009-02-10
Thanks, 

that was the 127.0.0.1 which was wrong.

I've set the server private ip (192.168.0.1) instead, and now it's working.

Also about this IP, my server is behind a router, And I'll need to backup remote client through SSH. What IP Should I put as DirAddress?  


Thomas.

---

### Post by Endwin on 2009-02-10
Strike what I said before.


I read the documentation better that sets what the directors listens on not where it allows connections from. You should be fine. =)

---

