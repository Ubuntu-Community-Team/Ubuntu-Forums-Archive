---
title: "fail to start BIND9"
date: 2009-07-04
forum: Server Platforms
---

### Post by elmusishian on 2009-07-04
Im new to Ubuntu, and i recently installed the server version on a desktop. I have been trying to configure it, but i am having problems trying to start BIND9. when i type: 

```
/etc/init.d/bind9 start
``` this is what i get in /var/log/syslog:
```

Jul  4 15:07:38 gusserver named[6577]: starting BIND 9.5.1-P2 -u bind
Jul  4 15:07:38 gusserver named[6577]: found 1 CPU, using 1 worker thread
Jul  4 15:07:38 gusserver named[6577]: using up to 4096 sockets
Jul  4 15:07:38 gusserver named[6577]: loading configuration from '/etc/bind/named.conf'
Jul  4 15:07:38 gusserver named[6577]: none:0: open: /etc/bind/named.conf: permission denied
Jul  4 15:07:38 gusserver named[6577]: loading configuration: permission denied
Jul  4 15:07:38 gusserver named[6577]: exiting (due to fatal error)

```thank you everybody in advance!

---

### Post by gombadi on 2009-07-04
> 
none:0: open: /etc/bind/named.conf: permission denied


What are the permissions of this file and the /etc/bind directory? 

```

ls -la /etc/bind

```

---

### Post by windependence on 2009-07-05
First of all, do you really need to run your own DNS? What are you going to use the server for?

-Tim

---

### Post by hzq1e on 2009-07-08
> **windependence said:**
> First of all, do you really need to run your own DNS? What are you going to use the server for?

-Tim

like me... just learn to know..
just have some experiment dude...:guitar:;)

---

### Post by drave99 on 2009-07-09
are you running as root ??

sudo /etc/init.d/bind9 start

---

