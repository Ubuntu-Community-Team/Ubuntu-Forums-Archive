---
title: "[SOLVED] Server is rejecting connections"
date: 2008-12-20
forum: Server Platforms
---

### Post by Mattventura on 2008-12-20
I have had a server running multiple services smoothly for the past month or so. However, now it seems to be rejecting all connections that are not from localhost on any port except 80 and 22. If I log into the server via ssh and connect to the ports locally, it works. I have tried removing the iptables firewall and it still doesn't work. It doesn't work when accessed from outside or inside the local network. On localhost, I can connect to all of my ports (22,25,80,143,445,6667,etc), but I cannot connect from any other host to the server through either of the server's network cards. I have also not found anything of interest in dmesg. Any suggestions as to how  I can fix this?

Update: When I am logged into the server, it will accept connections on 127.0.0.1 and localhost, but will reject connections on 192.168.1.110 and 192.168.1.111 (it's IPs). Additionally, if I access it through it's FQDN on any other host, it also fails.

Update: Solved. Some updates apparently reset some of my config files and I had to redo them.

---

