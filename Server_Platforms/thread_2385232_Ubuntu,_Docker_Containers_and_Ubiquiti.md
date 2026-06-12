---
title: "Ubuntu, Docker Containers and Ubiquiti"
date: 2018-02-17
forum: Server Platforms
---

### Post by falklan on 2018-02-17
Ubuntu Server 16.04 
[Ubiquiti UNMS]("https://unms.com/") | Ubiquiti [Unifi Controller]("https://help.ubnt.com/hc/en-us/articles/220066768-UniFi-How-to-Install-Update-via-APT-on-Debian-or-Ubuntu")

I am attempting to utilize subdomains for the aforementioned UBNT apps running on the same server. These apps are installed via docker containers. Neither nginx nor apache are running on this server. Both apps function properly and are accessible via FQDN w/port numbers. I have everything ready with the exception of internal routing to the different containers.

What I need to accomplish:

containerimageID1 = unifi.xxxx.com
containerimageID2 = unms.xxxx.com

I am not certain how to resolve this. Using either a nginx proxy, or deploying virtual proxy?

Any and all assistance is greatly appreciated!

---

