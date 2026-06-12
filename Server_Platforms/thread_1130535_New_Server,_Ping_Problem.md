---
title: "New Server, Ping Problem"
date: 2009-04-19
forum: Server Platforms
---

### Post by I3roknI3ottle on 2009-04-19
This is my first time setting up a ubuntu server and I'm doing it through the terminal.  I've been using this guide; [http://www.howtoforge.com/perfect-server-ubuntu8.04-lts](http://www.howtoforge.com/perfect-server-ubuntu8.04-lts), and after adjusting some settings I cannot ping the outside world.  When I do ping -c 5 [www.google.com](www.google.com), I get ping: unknown host [www.google.com](www.google.com).  If I try and ping my router or my laptop, I get responses.

I set my static up;
auto eth0
iface eth0 inet static
        address 192.168.1.121
        netmask 255.255.255.0
        network 192.168.1.0
        broadcast 192.168.1.255
        gateway 192.168.1.1

I made my hostname; dimension.example.com, would that be the problem?

---

### Post by BkkBonanza on 2009-04-19
If you can ping your router then most likely there's nothing wrong with your setup locally. My guess is that your router or isp are blocking ICMP. Check the router as you can change settings there to allow/disallow ICMP protocol. My isp blocks ICMP - not sure why but I have never been able to ping public ips. If yours does that then there's not much you can do about it on your systems.

Edit - Just saw your comment about unknown host. Probably not your hostname that's a problem but your nameserver lookup could be setup wrong. First check ping with a public ip value ie. ping 72.14.205.100 for google. If that works then don't worry about ping at the router etc. You need to check /etc/resolv.conf and make sure it has valid settings for name lookup. Typically you want to have your router's ip there and it will relay onto whatever dns server your isp provides. Doing it that way allows it to get updated if the isp changes nameservers.

/etc/resolv.conf:

nameserver 192.168.1.1

---

### Post by I3roknI3ottle on 2009-04-19
My main problem is whenever I try to do apt-get update or upgrade I get failed responses.

---

### Post by BkkBonanza on 2009-04-19
It sounds like you have name resolution problems. Try a quick check with,
**nslookup google.com**
If you don't get an ip value back then you need to look into your resolv.conf file and whether the problem is there or on your router.

---

### Post by I3roknI3ottle on 2009-04-19
nah it didnt respond with an ip

my resolv.conf is

search dimserver.example.com
nameserver 192.168.1.121

---

### Post by BkkBonanza on 2009-04-19
Take out the search line and change the 192.168.1.121 to 192.168.1.1
It should tell your machine to look for names on your router.
Then if it still doesn't work then check your router and make sure it is getting it's nameserver dynamically from the isp or has been set correctly with a static value.
It should relay name requests to your isp nameserver.

---

### Post by I3roknI3ottle on 2009-04-19
Wow thanks! That did it, after I took out the search line and changed the name server too 192.168.1.1, I was able to ping & update!! I guess when I was fooling around in the resolv.conf I put the wrong thing DOH.

---

