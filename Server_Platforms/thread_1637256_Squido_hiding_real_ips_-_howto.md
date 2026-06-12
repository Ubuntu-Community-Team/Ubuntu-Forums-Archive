---
title: "Squido hiding real ips - howto?"
date: 2010-12-04
forum: Server Platforms
---

### Post by dedok on 2010-12-04
Hello! I have installed squido into my ubuntu 8.04. It almost works perfectly but it wont hide my ip. When i go for an example to [www.myip.is](www.myip.is) it shows my real ip & host but says that i connected into that website via my proxy.

How i can hide my real ip with squido and use my server's ip as my ip.

---

### Post by koenn on 2010-12-04
never heard of this squido.
do you mean squid ?

---

### Post by dedok on 2010-12-04
> **koenn said:**
> never heard of this squido.
do you mean squid ?
Yes i mean squid not squido haha :D

---

### Post by koenn on 2010-12-04
look in squid.conf for the forwarded_for option, and turn it off.

---

### Post by dedok on 2010-12-10
I updated my ubuntu from 8.04 into 9.10. Also reinstalled squid. Again i managed to connect into my squid proxy but squido is not hiding my ip. I added that follow_x_forwarded_for allow all ("all" means ip's from 127.0.0.0-255.255.255.255). 

What im doing wrong?

---

### Post by iponeverything on 2010-12-10
I don't think you understand how it works.

if your squid server is running on same box that you are using, then what kind of magic do you think it would be using? It's ip is your ip.

If you use a squid proxy that is somewhere else, besides your machine, your ip address will show up being the ip of that squid proxy.

---

### Post by dedok on 2010-12-11
> **iponeverything said:**
> I don't think you understand how it works.

if your squid server is running on same box that you are using, then what kind of magic do you think it would be using? It's ip is your ip.

If you use a squid proxy that is somewhere else, besides your machine, your ip address will show up being the ip of that squid proxy.
I think that I understand how squid works. Im running squid on a dedicated server. I just want that squid hides my real ip when im surfing via squid.

---

### Post by iponeverything on 2010-12-11
Then it was me that didn't understand, apologies. 

do have:

```
forwarded_for off

```

in your squid.conf as suggested by koenn

See:
[http://www.nineteenlabs.com/2007/08/24/high-anonymous-proxy-squid-25/](http://www.nineteenlabs.com/2007/08/24/high-anonymous-proxy-squid-25/)

---

### Post by dedok on 2010-12-11
> **iponeverything said:**
> Then it was me that didn't understand, apologies. 

do have:

```
forwarded_for off

```in your squid.conf as suggested by koenn

See:
[http://www.nineteenlabs.com/2007/08/24/high-anonymous-proxy-squid-25/](http://www.nineteenlabs.com/2007/08/24/high-anonymous-proxy-squid-25/)
No problem mate and thanks for those instructions - problem solved. I still have a small question: My dedicated server has two ip's. How i can set my second ip into squid ip.

Example:
Current ip 114.114.114.114 and i see this as my ip in squido.
I have also another ip 89.89.89.89 and id like to use this, how i can do that :D

---

### Post by iponeverything on 2010-12-12
are the ip's on separate interfaces or primary and virtual interface?

in the squid.conf you should be specify the listening interface, if your second address is on a virtual interface -- try switching to make the primary the virtual address and vise-versa. 

I take it the addresses are just for example purposes and not the actual addresses. Are the two interface addresses in the same address range?

---

