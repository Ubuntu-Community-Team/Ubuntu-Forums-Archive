---
title: "Do I need a firewall??"
date: 2006-06-21
forum: Server Platforms
---

### Post by tisse on 2006-06-21
I have a small web and file server at home. The server runs Apache, PHP, mySQL, ssh, samba (no desktop though, it doesn't even have a monitor). It connects to the network through a router with a built-in firewall with port 80 and 22 open to Internet.

My question is if I need to install a firewall or any other security programs?

---

### Post by icheyne on 2006-06-21
Not really. The router will protect you from incoming traffic.

If you were on a Windows machine, I might recommend that you have a software firewall (e.g. Kerio) to detect outgoing connections from spyware, but that's not a problem for Linux.

---

### Post by tisse on 2006-06-21
Thank you.

I thought that would be the case but I was not really certain.

---

### Post by nkassi on 2006-06-21
Actually a firewall with iptables would not hurt. If it's too much trouble don't worry about it but it could be a nice learning opertunity. 

Nic

---

### Post by mushr00m on 2006-06-21
I found that when I was in the same place as you it was interesting to learn about using iptables, I started with firestarter and it went from there.

try 'man iptables' and see if that is something to learn.

mushr00m

---

### Post by tisse on 2006-06-22
I will have a look at iptables, thanks for the tip.

/Tisse

---

### Post by LordHunter317 on 2006-06-22
[QUOTE=nkassi]Actually a firewall with iptables would not hurt.[/quote]Actually it could, because it compicates network configuration for no gain.  You do no setup firewalls without need and reason.

---

