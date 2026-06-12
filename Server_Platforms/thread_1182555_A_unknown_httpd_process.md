---
title: "A unknown httpd process ??"
date: 2009-06-09
forum: Server Platforms
---

### Post by raghaven.kumar on 2009-06-09
Hi,
I have this when i do a netstat -tulpn
```
tcp        0      0 0.0.0.0:80              0.0.0.0:*    LISTEN      17565/apache2
tcp        0      0 0.0.0.0:443              0.0.0.0:*   LISTEN      17565/apache2
tcp        0      0 0.0.0.0:2200            0.0.0.0:*    LISTEN      17628/httpd -DSSL

```
and ps 17628 gives```
  PID TTY      STAT   TIME COMMAND
17628 ?        S      0:00 /usr/local/apache/bin/httpd -DSSL

```
but in /usr/local
```
root@server:/usr/local# ls
bin  etc  games  include  lib  man  sbin  share  src  usermin-1.370 usermin-1.400

```
as you can see theres no apache folder in this:confused:
but this httpd -DSSL runs alongside apache2.
Is it a anonymous process??

PS: I am using Ubuntu 8.04 server and Apache/2.2.8 (Ubuntu)

---

### Post by raghaven.kumar on 2009-06-12
Update: I found that DSSL process is running from the postgres user
Could it be a hackers doing?
```
root      2037  0.0  0.0   3004   764 pts/0    S+   16:04   0:00 grep postgres
postgres 20165  0.0  0.0   2216   584 ?        S    12:21   0:00 /usr/local/apache/bin/httpd -DSSL
                                                                          ? redone
```

Also why the "?redone" shows in the **ps aux | grep postgres**

---

### Post by raghaven.kumar on 2009-06-14
No one has a idea ??

---

### Post by wanderingtux on 2009-06-14
It shows up because the process is running as the postgres user. 

To your question of whether it is a hacker's doing, difficult to say unless you check if you have actually got apache2 installed on your system.

It is clear you are using postgres - not clear what you do with it.

---

### Post by wanderingtux on 2009-06-14
Shut down webmin that you are running and see if you still see the process.

---

### Post by raghaven.kumar on 2009-06-16
> **wanderingtux said:**
> 

It is clear you are using postgres - not clear what you do with it.

Hi man,
I am using postgres as the db backend.

And i have got the apache2 installed man.
Its a live production server.

Heres the output of webmin stop.
IMO, the culprit is not webmin.
```
root@server:~# /etc/init.d/webmin stop
Stopping Webmin server in /usr/share/webmin
root@server:~# netstat -tulpn
Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
tcp        0      0 0.0.0.0:80              0.0.0.0:*               LISTEN      8749/apache2    
tcp        0      0 0.0.0.0:2200            0.0.0.0:*               LISTEN      20165/httpd -DSSL  
root@server:~# ps aux | grep httpd
postgres 20165  0.0  0.0   2216   584 ?        S    Jun12   0:01 /usr/local/apache/bin/httpd -DSSL                                                                                                                                                                                                                        ? redone
root     21686  0.0  0.0   3008   776 pts/0    S+   15:13   0:00 grep httpd
```
Also, scroll to the rightmost of the code, whats that "?redone"
Why i doubt this a hackers do is cause theres no /usr/local/apache folder(See my first post in this thread)

---

