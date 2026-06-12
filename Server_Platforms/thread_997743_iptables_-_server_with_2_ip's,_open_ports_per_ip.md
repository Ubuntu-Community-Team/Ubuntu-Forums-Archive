---
title: "iptables - server with 2 ip's, open ports per ip"
date: 2008-11-30
forum: Server Platforms
---

### Post by PC_Nerd on 2008-11-30
Hi,

fairly new to running a server ( I'm used to using gnome etc).  I've been using iptables and at the moment i've got a default drop all connections except certain ports....  

my current server is a VPS server and has 2 Ip addresses to it.  What I wanted was to be able to open certain ports per IP address.  so for example:
IP1:80 - works
IP2:80 - fails
IP1:22 - fails
IP2:22 - works.....


or something along those lines. 

Thanks for your help,
PC_Nerd

---

### Post by iler on 2008-11-30
You should specify the destination in your iptables rules with --destination parameter. So something like this (included also some other useful parameters):
iptables -A INPUT -i eth0 -m state --state NEW -p tcp --dport 80 --destination IP2 --syn -m limit --limit 35/minute -j ACCEPT
[URL="http://linux.die.net/man/8/iptables"]
http://linux.die.net/man/8/iptables[/URL]

---

### Post by PC_Nerd on 2008-11-30
Ok - thats awesome thnaks

Also Is it safe/should I allow all outbound connections, or only specify what ports should be opened as per programs installed?  eg: at the moment i think im accidently blocking aptitude b blockign outbound port80..... Is it safe to unblock everything outbound?

Thanks

---

