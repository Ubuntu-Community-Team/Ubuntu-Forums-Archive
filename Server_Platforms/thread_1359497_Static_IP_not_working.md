---
title: "Static IP not working"
date: 2009-12-19
forum: Server Platforms
---

### Post by xtjacob on 2009-12-19
I'm trying to setup the static IP for my server. When I boot into it the only thing I can do is SSH into, and control it, but when I try to connect to the internet or ping Google it doesn't work until I run ```
dhclient eth0
```
but then it is assigned its own IP and is no longer static. How can I connect to the internet while keeping it with a static IP?

---

### Post by Cheesemill on 2009-12-19
As well as editing /etc/network/interfaces you have to put your DNS settings in /etc/resolv.conf

---

### Post by xtjacob on 2009-12-19
For DNS settings do you mean ```
nameserver 8.8.8.8
```?

---

### Post by Cheesemill on 2009-12-19
Yep, that's the one.

Can you post your /etc/network/interfaces and /etc/resolv.conf files for us to take a look at.

---

### Post by xtjacob on 2009-12-19
I got it to work by adding a assigned IP address with the mac on my router so it works now. :)

---

### Post by lisati on 2009-12-19
> **xtjacob said:**
> I got it to work by adding a assigned IP address with the mac **on my router** so it works now. :)

:) That's my preferred method too, letting my routers do their job handing out IP addresses.

---

### Post by xtjacob on 2009-12-19
Actually it's still static, I assigned, and reserved it so the router wouldn't get confused.

---

### Post by lisati on 2009-12-19
> **xtjacob said:**
> Actually it's still static, I assigned, and reserved it so the router wouldn't get confused.

I know. Both routers I have on my home network can assign static addresses to specific MAC addresses. I find it a lot easier than messing around at the computer end.

---

### Post by Iowan on 2009-12-20
> **xtjacob said:**
> Actually it's still static, I assigned, and reserved it so the router wouldn't get confused.
You may/(not) have done it this way, but I also am fond of letting the DHCP server assign a static lease to a machine (based on MAC address). The machine can be left configured for DHCP, but it will get the same address.

---

### Post by Vegan on 2009-12-20
I use static addressing for servers, DHCP for clients. My Linksys box is fine with both.

By default the DHCP is 100-150 but you can change it to what ever you want. I use 2-99 for static address servers and 100-254 for DHCP clients.

---

### Post by confusedstingray on 2009-12-23
A little confused do you want to be static via machine or router.
need some info the contents of /etc/network/interfaces
and the version of ubuntu. 
then we can help set your ip

---

