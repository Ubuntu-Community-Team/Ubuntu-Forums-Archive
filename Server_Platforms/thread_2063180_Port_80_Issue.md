---
title: "Port 80 Issue"
date: 2012-09-26
forum: Server Platforms
---

### Post by sporanox on 2012-09-26
I am running a VPS, I installed apache.  The httpd service is running, but I cannot get a web page.  On the local machine if I telnet  127.0.0.1 80 I get connection refused.  Any ideas?

---

### Post by CharlesA on 2012-09-26
Check the firewall.

```
sudo iptables -L
```

---

### Post by sporanox on 2012-09-26
> **CharlesA said:**
> Check the firewall.

```
sudo iptables -L
```

This is what I get

> 
computer:~# sudo iptables -L
Chain INPUT (policy ACCEPT)
target     prot opt source               destination
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:www
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:www
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:www
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:www

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination
root@roadrunner:~#


---

### Post by lykwydchykyn on 2012-09-26
I would imagine /var/log/apache2/error.log could be enlightening.  /var/log/syslog might also.

also
```

sudo netstat -tnap

```

Could tell you if apache is listening on any ports.

---

### Post by sporanox on 2012-09-26
> **lykwydchykyn said:**
> I would imagine /var/log/apache2/error.log could be enlightening.  /var/log/syslog might also.

also
```

sudo netstat -tnap

```

Could tell you if apache is listening on any ports.



netstat -tnap
```


# sudo netstat -tnap
Active Internet connections (servers and established)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
tcp        0      0 0.0.0.0:22              0.0.0.0:*               LISTEN      1243/sshd
tcp        0      0 127.0.0.1:25            0.0.0.0:*               LISTEN      1290/sendmail: MTA:
tcp        0      0 127.0.0.1:587           0.0.0.0:*               LISTEN      1290/sendmail: MTA:
tcp        0      0 222.22.222.222:22       111.111.111.111:56618     ESTABLISHED 9398/sshd: root@tty
tcp        0    300 222.22.222.222:22       111.111.111.111:57179     ESTABLISHED 9470/sshd: root@tty
tcp6       0      0 :::22                   :::*                    LISTEN      1243/sshd
:~#

```

---

### Post by CharlesA on 2012-09-26
The service isn't running. Check the apache log and see what it says.

---

### Post by sporanox on 2012-09-26
> **CharlesA said:**
> The service isn't running. Check the apache log and see what it says.

If I run /etc/init.d/apache2 start

This is the result
> Computer:~# /etc/init.d/apache2 start
 * Starting web server apache2                                                  WARNING: MaxClients (10) must be at least as large
 as ThreadsPerChild (25). Automatically
 increasing MaxClients to 25.
                                                                         [ OK ]

---

### Post by CharlesA on 2012-09-26
Check netstat again.

---

### Post by sporanox on 2012-09-26
> **CharlesA said:**
> Check netstat again.

same result

> 
tcp        0      0 0.0.0.0:22              0.0.0.0:*               LISTEN      1243/sshd       
tcp        0      0 127.0.0.1:25            0.0.0.0:*               LISTEN      1290/sendmail: MTA:
tcp        0      0 127.0.0.1:587           0.0.0.0:*               LISTEN      1290/sendmail: MTA:
tcp6       0      0 :::22                   :::*                    LISTEN      1243/sshd       




---

### Post by sporanox on 2012-09-26
Apache Error Log

> 
root@computer:~# tail -f  /var/log/apache2/error.log
[Thu Sep 27 00:35:37 2012] [alert] (11)Resource temporarily unavailable: apr_thread_create: unable to create worker thread
[Thu Sep 27 00:35:39 2012] [alert] No active workers found... Apache is exiting!
[Thu Sep 27 00:35:57 2012] [warn] pid file /var/run/apache2.pid overwritten -- Unclean shutdown of previous Apache run?
[Thu Sep 27 00:35:57 2012] [notice] Apache/2.2.14 (Ubuntu) configured -- resuming normal operations
[Thu Sep 27 00:35:57 2012] [alert] (11)Resource temporarily unavailable: apr_thread_create: unable to create worker thread
[Thu Sep 27 00:35:59 2012] [alert] No active workers found... Apache is exiting!
[Thu Sep 27 00:36:18 2012] [warn] pid file /var/run/apache2.pid overwritten -- Unclean shutdown of previous Apache run?
[Thu Sep 27 00:36:18 2012] [notice] Apache/2.2.14 (Ubuntu) configured -- resuming normal operations
[Thu Sep 27 00:36:18 2012] [alert] (11)Resource temporarily unavailable: apr_thread_create: unable to create worker thread
[Thu Sep 27 00:36:20 2012] [alert] No active workers found... Apache is exiting!


---

### Post by CharlesA on 2012-09-26
Check here:
[http://serverfault.com/questions/137769/apache2-is-not-starting-my-webserver/137782#137782](http://serverfault.com/questions/137769/apache2-is-not-starting-my-webserver/137782#137782)
[http://woshka.com/blog/apache/how-to-fix-resource-temporarily-unavailable-apr_thread_create-unable-to-create-worker-thread-on-apache.html](http://woshka.com/blog/apache/how-to-fix-resource-temporarily-unavailable-apr_thread_create-unable-to-create-worker-thread-on-apache.html)

---

