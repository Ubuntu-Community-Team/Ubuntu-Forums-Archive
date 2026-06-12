---
title: "Apache 2 wont start"
date: 2014-03-14
forum: Server Platforms
---

### Post by stevetingate on 2014-03-14
Hi I am having trouble restarting Apache, I get the error
```
(99)Cannot assign requested address: make_sock: could not bind to address 58.108.248.95:80
no listening sockets available, shutting down
Unable to open logs
Action 'start' failed.
The Apache error log may have more information.
```
when I run the command
```
sudo netstat -ltnp | grep ':80'
```
this is what I get:
```
tcp   0  0 127.0.0.1:8080  0.0.0.0:*    LISTEN      2320/python
```
if I clear the port using
```
sudo kill -9 2320
```
and then restart apache2 I still get the same error
if anyone has any info it would be greatly appreciated !!!

---

### Post by lisati on 2014-03-14
*Thread moved to **Server Platforms**.*

---

### Post by Lars Noodén on 2014-03-14
How are you trying to start Apache2 and what does the end of the error log say?

```

tail /var/log/apache2/error.log 

```

---

