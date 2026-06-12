---
title: "can't connect past localhost - Apache 2 Webserver Issue -"
date: 2009-10-06
forum: Server Platforms
---

### Post by wiseguy12851 on 2009-10-06
I can't connect past localhost on my ubuntu desktop edition computer, it works fine on my desktop locally but as soon as I enter on another computer http:// and the ip address of my computer it displays page not found (the 404 error page), I'm discussing LAN not over the internet.

I'm thinking it's a firewall issue but I have spent the last few hours trying to get by this including the recent hour and a half trying to find out if it's even related to firewalls cluttering up my computer with software (verified of course)

windows software developer/programmer leaving into the linux world as of 3 days ago so I'm still getting used to things

---

### Post by Iowan on 2009-10-06
It's possible that Apache is listening only n 127.0.0.1. See if any of the troubleshooting hints [here]("https://help.ubuntu.com/community/ApacheMySQLPHP#Troubleshooting%20Apache") help.

---

