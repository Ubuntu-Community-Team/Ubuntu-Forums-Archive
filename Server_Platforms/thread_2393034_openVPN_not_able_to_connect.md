---
title: "openVPN not able to connect"
date: 2018-05-28
forum: Server Platforms
---

### Post by kaydeejay on 2018-05-28
Hello everyone! I'm trying to set up my VPN configurations, I use bolehvpn. I set up the configuration files but I can't seem to connect to anything. Another friendly user showed me how to grab a .log file but didn't know what to look for, so I figured I'd post it here and see if anyone is willing to take a look.    .log file: [https://pastebin.com/DMiEbu7A](https://pastebin.com/DMiEbu7A)  Operating system and version: Ubuntu 18.04 Hardware: Dell Latitude E7440  Thanks in advance!

---

### Post by wildmanne39 on 2018-05-28
*Thread moved to **Server Platforms for a more appropriate fit**.*

---

### Post by darkod on 2018-05-29
You control only the client, the openvpn server is not managed by you, right?

It would be helpful to post the .conf file you are using on the client, instead of the full log.

But one thing I see in the log is that adding static routes is failing. Probably because the openvpn client is not running as root and does not have permissions to create the routes.

How are you opening the connection, manually or with a .conf file in /etc/openvpn?

---

