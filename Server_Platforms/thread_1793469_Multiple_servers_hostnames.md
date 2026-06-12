---
title: "Multiple servers hostnames"
date: 2011-06-29
forum: Server Platforms
---

### Post by peekaboo on 2011-06-29
I have 2 servers on my home network and one server on a different network.  All running Ubuntu Server.
I connect to the servers using Putty.
I can connect to my first server by typing "servername1" but not to my second server.  I always have to type the ip address of the second server in order to connect.
I use a DNS service (DynDNS) in order to connect to the third server.
How do I make the second server respond to its hostname ("servername2") so I don't have to type its ip address (192.168.1.xxx) every time?
Is there a way to make the server that's on a different network entirely respond to its hostname (or another name) without going through an external DNS service?

Thanks.

---

### Post by rubylaser on 2011-06-29
Assuming your using Windows for your OS, you could just make an entry in your hosts file for the hostname you'd like.  Or, the better solution is to setup the hostname record on your home network's router.

---

### Post by peekaboo on 2011-06-29
> **rubylaser said:**
> Assuming your using Windows for your OS, you could just make an entry in your hosts file for the hostname you'd like.  Or, the better solution is to setup the hostname record on your home network's router.
I am using windows7x64.
Can you guide me on how to make the entry in my hosts file or properly setup the hostname record on my router (Dlink DI 604)?
Why does my first server respond to its hostname but not my second server?

---

### Post by Lloyd_mcse on 2011-06-29
Windows Host files is in..
 
C:\windows\system32\drivers\etc\
 
and you would add..
 
192.168.1.xxx  domain.com
 
(where 192.168.1.xxx is your server ip)

---

### Post by peekaboo on 2011-06-29
> **Lloyd_mcse said:**
> Windows Host files is in..
 
C:\windows\system32\drivers\etc\
 
and you would add..
 
192.168.1.xxx  domain.com
 
(where 192.168.1.xxx is your server ip)

Thanks, that works.
I wish I knew why one server worked before and still does (without being included in the hosts file) while the second one didn't.

---

### Post by collisionystm on 2011-06-29
> **peekaboo said:**
> Thanks, that works.
I wish I knew why one server worked before and still does (without being included in the hosts file) while the second one didn't.


You need to manage your DyDNS to make sure there is a record for all your servers.

---

