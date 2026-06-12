---
title: "BIND DNS memory consuming"
date: 2010-11-13
forum: Server Platforms
---

### Post by Smart_Viral on 2010-11-13
hey geeks

in my new openvz vps i noted that bind9 is taking a lot of the RAM

process info:
ID    Owner Size    	Command   
17559 root  290396 kB 	/usr/sbin/named -c /etc/bind/named.conf

can anybody help?

---

### Post by Smart_Viral on 2010-11-14
284mb ... isn't that too much!???

---

### Post by KB1JWQ on 2010-11-14
That depends; how many zones are you serving DNS for?

One also wonders why your named service is running as root.

---

### Post by James78 on 2010-11-15
@KB1JWQ: Excellent point. The default user it should run as is BIND.

---

### Post by SeijiSensei on 2010-11-15
For comparison purposes, I'm serving 34 zones and using about 65MB. This is on CentOS 5.5 using bind 9.3.6.

---

### Post by KB1JWQ on 2010-11-15
> **James78 said:**
> @KB1JWQ: Excellent point. The default user it should run as is BIND.

Weird, I usually see it running as "named" albeit not on Ubuntu. :-)

---

### Post by SeijiSensei on 2010-11-15
> **KB1JWQ said:**
> Weird, I usually see it running as "named" albeit not on Ubuntu. :-)

It runs as user "named" on RedHat-flavored distros; on Ubuntu (and probably Debian?) it runs as user "bind".

---

### Post by James78 on 2010-11-15
> **KB1JWQ said:**
> Weird, I usually see it running as "named" albeit not on Ubuntu. :-)
Here's my ps output.
```
toonarmy@ns1:~$ ps -fC named
UID        PID  PPID  C STIME TTY          TIME CMD
bind       872     1  0 Nov14 ?        00:00:02 /usr/sbin/named -u bind
```

---

### Post by Smart_Viral on 2010-11-15
> **KB1JWQ said:**
> That depends; how many zones are you serving DNS for?

One also wonders why your named service is running as root.

after the first reboot,,, service name has became "bind" instead of "root"

> **SeijiSensei said:**
> For comparison purposes, I'm serving 34 zones and using about 65MB. This is on CentOS 5.5 using bind 9.3.6.

LOL, i just have 6 zones:

mywebsite.com 
Root zone
0
127
255
localhost

(on ubuntu server 10.04 and bind 9.7.0)

---

### Post by James78 on 2010-11-15
I'm serving 24 zones. Most of them are just empty zones, such as 168.192.in-addr.arpa., mainly because I found out in my security log that BIND was actually leaking queries, (see, "What does "RFC 1918 response from Internet for 0.0.0.10.IN-ADDR.ARPA" mean?" in the below link), and adding those empty zones fixed it. Because I found out about that, I actually recommend everyone enable the zones.rfc1918 file...

named.conf.local
```
// Consider adding the 1918 zones here, if they are not used in your
// organization
//include "/etc/bind/zones.rfc1918";
```

[http://www.bind9.net/BIND-FAQ](http://www.bind9.net/BIND-FAQ)

---

### Post by Smart_Viral on 2010-11-27
thanks for the tips James78

---

### Post by MagnuzMaximuz on 2011-08-30
Hi,

I'm sorry for bumping such old thread. I was having similar problem and I just spent hours in frustration before I finally find the fix.

So I think I'll share it :)

By default BIND (or named) *_should_* create several cpus worker threads to take advantage of multiple CPUs. If not specified, named will try to determine the number of CPUs present and create one thread per CPU. If it is unable to determine the number of CPUs, a single worker thread will be created.

But in my case it creates no less than 10s memory-hungry processes, so that's the problem. 

I fixed it by editing ```
/etc/sysconfig/named
```  

Add:
```
OPTIONS="-n 1"
```

Basically that will tell named to create fixed no. process of each processor.

and Voila named RAM usage went from 128 mb too 60 mb-ish.

Hope this will be useful. :P

---

