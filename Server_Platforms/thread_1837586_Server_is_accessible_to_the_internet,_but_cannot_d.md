---
title: "Server is accessible to the internet, but cannot download/ping"
date: 2011-09-02
forum: Server Platforms
---

### Post by chekt on 2011-09-02
I'm running Ubuntu server edition 11.04 with LAMP + ftp + openssh, fully updated. It is set up with the external IP of 173.66.247.139 (which sends you to the default apache webpage). The ip is 192.168.1.10, set to be static by the router, which also has it DMZ'd. The firewall on the server is currently disabled. It can ping the router, but it cannot ping any external address or download anything. This is the routing table: [http://pastebin.com/NmH8Cb4P](http://pastebin.com/NmH8Cb4P).
I had this problem when I first installed the server a day ago, but I solved it be doing a clean install. It was working fine, until just recently when I tried to download something and it didn't work. It's running through eth0. I haven't messed with the networking settings at all server-side. The physical arrangement is that it's running through a modem to the router. The router is a verizon one (and I suspect it may be the cause of these issues, but I'm not qualified to say). Any ideas what the problem might be?

---

### Post by chekt on 2011-09-02
This is what ifconfig shows: [http://paste.ubuntu.com/680736/](http://paste.ubuntu.com/680736/)

Let me clarify, the server has a static IP from the router (192.168.1.10), which is also the address which is DMZ'd. The external IP is the external IP of the router, and is there to show that you can connect to it from the internet. It can be pinged from the external address, but the server cannot ping external addresses.

These are pictures of how I set up the server with the router: [http://imgur.com/a/6TGVL#2hvgz](http://imgur.com/a/6TGVL#2hvgz). The first picture shows the device info. When the router is told to ping the server, it DOES get a response. The next two are of how I DMZ'd it and how I made the IP static, if those are any help.

EDIT: You can also SSH into it from the external IP, but it still won't ping outside IPs. This is really confusing.

---

### Post by chekt on 2011-09-02
Ok, the problem was with the verizon router setting its static IP. I have no idea how that caused the problem, but once I disabled the server's static IP, it could access the internet again.

---

