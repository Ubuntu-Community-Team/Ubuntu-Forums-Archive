---
title: "Problem with ssh"
date: 2006-01-09
forum: Server Platforms
---

### Post by Cyonix on 2006-01-09
Hi,

I'm currently using an ubuntu box as (amongst other things) a router for serving the internet to a local area network. The box has eth0 and eth1 fitted, with eth0 connected to the local area network and eth1 connected to a cable modem. For some reason I can't fathom, if eth1 looses connection to the internet ssh stops responding to a connection request from within my local area network. I can ping the server and if I nmap the box from within my network ssh appears to still be running on port 22. If anyone could offer me any help on this I'd greatly appreciate it, as I don't have a monitor and keyboard plugged into the box and its very annoying not having ssh access when I most need it. ie when somethings gone wrong ;) 

Thanks.

---

### Post by Cyonix on 2006-01-10
After some further investigation, I found that I can log into the box. I just need to leave an ssh client connecting for over 5 minutes. If I try and connect to sshd using an ssh client on my ubuntu box it connects straight away, using either 127.0.0.1 or the eth0 adapter address. Could this have something to do with my firewall rules and the fact that I'm using IP MASQ with one of the adapters not connected?

Thanks.

---

