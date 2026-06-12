---
title: "When Port Forwarding, Should One Open All Ports?"
date: 2016-12-26
forum: Server Platforms
---

### Post by cook150 on 2016-12-26
When Port Forwarding (for a web server), should one open all ports? Apparently, my router will change a device's IP Address only if all ports are opened to a Public IP. However, I'm unsure if my IP Address is public or not. How do I find out?

---

### Post by TheFu on 2016-12-26
No. You should point the specific port and specific type of traffic (tcp/udp) to the specific LAN static IP of the server. The server MUST have a static IP for this to work.

Private/LAN IPs are well-documented. Look on [wikipedia]("https://en.wikipedia.org/wiki/Private_network") (or anywhere else) for those. If the IP is in any of those private ranges, then it is not public and won't be routed on the internet.  10.x.x.x/8, 172.16.x.x/12 and 192.168.x.x/16 are those ranges. If you don't understand that notation, you'll want to learn it.

Get used to searching for answers for stuff like this. It would be best to get an introductory text on the subject and read it, so all the incorrect answers on the internet by people who don't really understand can be recognized. That applies to Linux and apache and DBs too.  There's lots of miss-information out there and lots of not-quite-correct information.

---

### Post by cook150 on 2016-12-26
Thank you so much for the help!

---

