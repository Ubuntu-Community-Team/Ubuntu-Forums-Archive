---
title: "Accessing subpage on Apache server with NAT reflection/Hairpin NAT"
date: 2013-06-13
forum: Server Platforms
---

### Post by MadsRC on 2013-06-13
I got myself an Apache server running on my Ubuntu server in my private datacenter here at home.

Currently I run a PFSense firewall where port 80 is NAT'ed to my webserver.

I had a problem accessing my page from my LAN on my domainname (say home.example.com) which before I fixed by setting up a private DNS server on my LAN. That wasn't a great solution though, so when I found out my firewall could take NAT Relflection into account, I enabled that and removed my DNS server.

Problem now is that while I can access my domain (home.example.com) but if I access a subpage, say home.example.com/randomfolder I get a 404 - But going to that address from outside my LAN, I get the content of said folder.

Anyone have any idea what is wrong?

---

### Post by MadsRC on 2013-06-13
Acctually resolved it myself... Stupid me had forgotten that the directory rewrote the domain to a HTTPS, and that I had forgotten to enable DNS reflection for HTTPS port :P

---

