---
title: "plz tell me the configuration of dns"
date: 2008-03-23
forum: Server Platforms
---

### Post by fnkhan on 2008-03-23
i want to create a simple dns server in ubuntu server command line
if i entered nslookup
>190.160.0.3
it define the abc.com
if i entered nslookup
>abc.com
it define the 190.160.0.3

i m new in linux plz send me the configuration

---

### Post by ghost_ryder35 on 2008-03-23
[http://www.ubuntugeek.com/dns-server-setup-using-bind-in-ubuntu.html](http://www.ubuntugeek.com/dns-server-setup-using-bind-in-ubuntu.html)

---

### Post by fnkhan on 2008-03-23
after using these website i m confuse
what is ns and forworder

---

### Post by ghost_ryder35 on 2008-03-23
this may help
[http://ubuntuforums.org/showthread.php?t=236093](http://ubuntuforums.org/showthread.php?t=236093)
and
[http://en.wikipedia.org/wiki/Domain_name_system](http://en.wikipedia.org/wiki/Domain_name_system)

---

### Post by fnkhan on 2008-03-23
i already used this configuration but there is an error for 
/etc/init.d/bind9 
connection failed to 127.0.0.1
why this show the 127.0.0.1 
i configured dns in the ip 190.160.0.3

---

### Post by ghost_ryder35 on 2008-03-23
> **fnkhan said:**
> i already used this configuration but there is an error for 
/etc/init.d/bind9 
connection failed to 127.0.0.1
why this show the 127.0.0.1 
i configured dns in the ip 190.160.0.3
127.0.0.1 is the address of your local machine (i.e. whatever machine you are getting that error message on) your DNS server needs to point to itself for DNS.  I am confused on what you are asking.

---

### Post by fnkhan on 2008-03-23
127.0.0.1 is a local host right
my system ip is 190.160.0.3
i want to enter nslookup
>190.160.0.3
this shows abc.com
r u understand or not

---

### Post by spiderbatdad on 2008-03-23
4.2.2.1
4.2.2.6

---

### Post by ghost_ryder35 on 2008-03-23
> **spiderbatdad said:**
> 4.2.2.1
4.2.2.6
gotta love those public servers :)

---

### Post by Sef on 2008-03-23
Moved to Server Platforms.

---

