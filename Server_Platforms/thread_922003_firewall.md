---
title: "firewall"
date: 2008-09-16
forum: Server Platforms
---

### Post by sfong15 on 2008-09-16
I've installed shorewall on a 7.10 VPS, now setting up another server on 8.04.  The latest shorewall I got from apt-get has marked improvement, i.e. very little changes I need at the example files except 'rules'.   After checking and changing the files, how do I start it and make shorewall to start at boot?

Googled a bit couldn't find much useful howto.

---

### Post by cariboo on 2008-09-17
I would assume that if shorewall was installed from the repositories that it should be configured to start up at boot. If not have a look at this thread:

[http://ubuntuforums.org/showthread.php?t=128301](http://ubuntuforums.org/showthread.php?t=128301)

Jim

---

### Post by sfong15 on 2008-09-17
> **cariboo907 said:**
> I would assume that if shorewall was installed from the repositories that it should be configured to start up at boot. If not have a look at this thread:

[http://ubuntuforums.org/showthread.php?t=128301](http://ubuntuforums.org/showthread.php?t=128301)

Jim

Thanks Jim, I have rebooted my server I presume one other way to check is trying to 'ssh in' via a not_allowed port.

---

### Post by sfong15 on 2008-09-17
> **sfong15 said:**
> Thanks Jim, I have rebooted my server I presume one other way to check is trying to 'ssh in' via a not_allowed port.

Does anyone know anyway to test if firewall is working from the outside?

---

### Post by gishaust on 2008-09-18
I use this I don't know if it the best. 

[https://www.grc.com/x/ne.dll?bh0bkyd2](https://www.grc.com/x/ne.dll?bh0bkyd2)

there is also nmap but I have not used it but people use it scan ports

---

### Post by baeksu on 2008-09-18
> **gishaust said:**
> I use this I don't know if it the best. 

[https://www.grc.com/x/ne.dll?bh0bkyd2](https://www.grc.com/x/ne.dll?bh0bkyd2)

there is also nmap but I have not used it but people use it scan ports

The problem with grc "Shields Up" test is that if you're behind a NAT router, it will only be able to test the external interface of that router.

To test inside your local network, you can do a simple 'nmap <ip_address>'. You can even do a 'nmap 192.168.1.1-255' to scan all machines within the 192.168.1.x subnet, which is pretty neat.

These two commands will scan the most common ports. To scan all 65k ports, do a 'nmap -p- <ip_address>'.

You can even do an nmap scan from the machine you are scanning.

One thing to note, though, is that if some ports are open to only a specific ip address, you won't see them unless you scan from those addresses.

---

### Post by windependence on 2008-09-18
IMHO, a hardware firewall is much better than running a firewall on your server. I don't run any siftware firewalls on my web servers because if someone decides to flood you server in a DDOS attack, they can take your machine down without even breaking in just because your firewall is using all your CPU or memory. You might want to build a firewall box from and old PC. Otherwise, most SOHO and home routers already have a decent firewall built in.

-Tim

---

### Post by sfong15 on 2008-09-18
> **windependence said:**
> IMHO, a hardware firewall is much better than running a firewall on your server. I don't run any siftware firewalls on my web servers because if someone decides to flood you server in a DDOS attack, they can take your machine down without even breaking in just because your firewall is using all your CPU or memory. You might want to build a firewall box from and old PC. Otherwise, most SOHO and home routers already have a decent firewall built in.

-Tim

It's a VPS that I'm trying to protect, I can't put a hardware firewall in front of my server.

---

