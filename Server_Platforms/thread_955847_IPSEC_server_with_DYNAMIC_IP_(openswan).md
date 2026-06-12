---
title: "IPSEC server with DYNAMIC IP (openswan)"
date: 2008-10-22
forum: Server Platforms
---

### Post by stbe on 2008-10-22
Hi, is there any help how to setup IPSEC using dynamic IP addresses? I could not find any useful introduction/howto yet.

Server machine (hardy) is reachable via internet using some dynamic IP with DynDNS entry. So I could enter it's address into client's config. I want to access server using mobile devices/laptops only speaking IPSEC. Those mobile devices have dynamic IP, too (and no fixed DNS name, dial-in). Something like "dial into intranet". Is this possible at all?

What are the software packages to look for (openswan...) and are there any guides or how to pages (or usable man pages) how to setup something like this? 

Unfortunately OpenVPN and PPTP (both easier to setup) is no option here.

---

### Post by Kadin2048 on 2008-10-22
Just wanted to say I am looking for a way to do the same thing.  I have been looking for a few days and I am getting discouraged; I'm really not sure if it's possible to do.

The closest I have heard people getting is by writing little scripts that continuously poll (via DNS queries) and figure out when the server's IP changes, and then re-write the IPsec/Racoon configuration files on the fly.  This approach is taken by Monowall I think, at least in some newer versions.  I think it's kind of a hack, to be honest.

I'd love to hear if there is a better way, but I can't figure out how to get around the syntax of the ipsec-tools.conf file, which seems to require that your server know its own IP and for that IP to be static, in order to write an instruction like:
```
spdadd server-ip-address 0.0.0.0 any -P out ipsec
           esp/tunnel/server-ip-address-0.0.0.0/require;
spdadd 0.0.0.0 server-ip-address any -P in ipsec
           esp/tunnel/0.0.0.0-server-ip-address/require;
```

I may give it a try setting up a "Roadwarrior config" (which is what I want/need) with 'localhost' in there as the server IP, but I do not have any faith that will work.  The assumption that the server knows its address is just built in too deeply I think.

EDIT:  [Here is the post]("http://osdir.com/ml/security.firewalls.m0n0wall/2003-08/msg00127.html") describing how Monowall apparently solves the problem.

---

