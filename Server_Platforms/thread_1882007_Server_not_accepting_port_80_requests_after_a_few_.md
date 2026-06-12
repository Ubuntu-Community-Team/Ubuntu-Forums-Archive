---
title: "Server not accepting port 80 requests after a few hours"
date: 2011-11-16
forum: Server Platforms
---

### Post by gypsumwolf on 2011-11-16
I have:

ISP
 |
 |
Router-----Server
 |
 |
Desktop

---
Server running Kubuntu 11.10 + Apache + Other stuff.
Desktop running Kubuntu 11.10
Router forwarding TCP and UDP port 80 and 22 to server. MTU set at 1500. WAN speed set at 100mbps.
---

After a few hours of inactivity internally on the LAN from all PCs, the website and ssh does not respond from a remote location.

If there server is not responding and someone opens a webbrowser on the internal Desktop PC that goes to a website, then right away my server accepts port 80 and ssh with no hesitation. This is the 2nd router (2 different companies) that this same issue occurred with.

--
Is it my Router?
Is it my ISP?
--
var/syslog shows nothing of suspicion.
--
The servers power settings do not allow it to sleep or powersave of any kind except LCD powering off.
--
The server responds too quickly after a webrowser is opened internally on the network on a nother PC for it to be an issue with power or anything like that.
--
Any ideas?

---

### Post by gypsumwolf on 2011-11-20
Sort-of solved. It it either my router or my ISP. But, I installed DD-WRT on my router which has the "Keep Alive" option and it is working just finew with that option. My routers original firmware had no keep alive option.

---

### Post by krishna.ub on 2011-11-20
Check firewall at server. Allow TCP and UDP for port 80

---

