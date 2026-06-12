---
title: "Second server added but can't access using &lt;hostname&gt;.local"
date: 2011-12-10
forum: Server Platforms
---

### Post by matthewboh on 2011-12-10
I just added a second server and everything works fine, but I want it to broadcast it's name on the LAN so I can connect to it using <hostname>.local

It's getting all the network connections, I can even get out to the Internet - I can also look up the IP address using nmap - where should I be looking for documentation, etc?

Thanks

---

### Post by papibe on 2011-12-10
The service responsible for 'zero configuration' (.local domain) is called avahi.

To check if it is installed:
```
apt-cache policy avahi-daemon 
```
To see if it's running:
```
ps aux | grep avahi
```
To restart the service:
```
 sudo service avahi-daemon restart
```
Here's more detail [information]("https://help.ubuntu.com/community/HowToZeroconf").

Hope it helps.
Regards.

---

### Post by matthewboh on 2011-12-11
Perfect! Thanks!

---

