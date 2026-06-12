---
title: "Help on 10.04"
date: 2010-12-20
forum: Server Platforms
---

### Post by drndrw on 2010-12-20
Hey everyone. I currently have a VPS at burst.net. I'm trying to get a website setup, and I have my web server installed, but I have no idea how to get my domain name setup with it. Does anyone know of any documentation on how to setup nameservers with a VPS? I'm sure this is a really easy answer, I'm kind of a newbie to linux. Thanks!

---

### Post by sapremias on 2010-12-21
If you are planning on running your own name service, look at several of the packages in the app repo and read the documentation on how to set each one up. You may consider BIND or PowerDNS. You might want to check out this thread...
[http://ubuntuforums.org/showthread.php?t=236093](http://ubuntuforums.org/showthread.php?t=236093)

If you are planning on letting some other service host your DNS, then you only need to know the IP address(es) of your server(s) that need to be pointed to by their DNS servers. Each service has their own instructions for setting up your DNS zone records.

Doesn't really matter that its a VPS unless they restrict certain activity from running from their virtual machines.

---

### Post by drndrw on 2010-12-22
Alright, well I checked and I have two IP addresses listed for my nameservers. This is probably a silly question, but my DNS host godaddy won't let me use these for nameservers. I tried setting up A record for ns1 and ns2 using these IP addresses, but no luck. How can I use these IP addresses for nameservers?

---

### Post by Bucky Ball on 2010-12-22
Godaddy can be problematic. :)

---

### Post by drndrw on 2010-12-22
True, but I guess I'm a bit stuck at this point :D. Any ideas?

---

