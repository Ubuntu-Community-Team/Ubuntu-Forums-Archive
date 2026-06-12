---
title: "Attaching an Ubuntu Server (with LAMP) to a windows network"
date: 2010-10-30
forum: Server Platforms
---

### Post by Glencore on 2010-10-30
I am sure there is a nice guide out there somewhere but I cannot find it. My question is:

The company I work for has a fully windows environment, servers and clients. The current server is on a Windows 2000 Server and I plan on replacing that. I wish to use Ubuntu server with Joomla for this purpose. This is my first venture into a purely command line interface, although I have played around with Ubuntu desktop in the past. My first question right now is: How do I log onto the Windows Network (active directory) from the ubuntu server. eth0 is reporting a valid internal IP on the network, so its been picked up okay. 

Edit: I also want to assign a static internal IP address instead of grabbing from the DHCP.

Edit2: Thinking about it, as the ubuntu server and windows server can ping each other do I even need to log into the domain? The server will only be serving web pages.

Kind Regards,
Glen

---

### Post by Boondoklife on 2010-10-30
If the server is just a web server, I can't see why you would need it to have AD logins unless your sites logins are to be controlled by AD accounts.

As far as the static IP, why not just set the DHCP server to give the box the same ip based on its MAC address.

---

### Post by CharlesA on 2010-10-30
If it's just a web server, you wouldn't have to do anything with active directory.

Just login with the shell account on that box to do admin task, otherwise just work with the joomla interface.

---

### Post by Glencore on 2010-10-30
Okay, thank you for the advice guys.

---

