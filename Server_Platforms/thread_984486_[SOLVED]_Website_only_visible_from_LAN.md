---
title: "[SOLVED] Website only visible from LAN"
date: 2008-11-16
forum: Server Platforms
---

### Post by glacialfury on 2008-11-16
I recently setup an ubuntu server with the default LAMP task.  For the most part, I left the default configuration alone.  The website is installed properly and runs from the server (localhost).  After configuring it to use port 192 (80 is blocked by my ISP), both on the router and apache, it now works over the LAN as well.  However, I cannot access it from the internet or an outside computer.

What is:
 - Ubuntu Server 8.10
 - Default LAMP install (apache2, php5, mysql5)
 - website locally viewable and over LAN
 - static IP from the router; server has internet access
 - alternate port used (192 instead of 80)
 - port is forwarded on the router to the correct IP

What is not:
 - cannot connect to website outside of LAN; receives a "...site seems valid but unable to establish a connection..." message.

Please offer any advice you can.  My first assumption is that it's router related.  The router is one of those Verizon router-modems used for their FiOS connections.  However, I don't know enough about configuring this sort of thing to say for sure.

---

### Post by Iowan on 2008-11-16
I'm certainly no expert on webserver setup, but I'd agree that it seems to be a router issue since you report that you can connect to it from inside the LAN.

---

### Post by cariboo on 2008-11-16
Are you using a static ip address on your server, or have you set up a long lease for it's dhcp address. The reason being, if you have an ip address on the server that changes occasionally, you will have to change the port forwarding accordingly.

Jim

---

### Post by vpsville on 2008-11-16
Its definately a router issue.

Try forwarding port 22 (ssh) and try connecting from the internet to port 22.  That may give you more meaningful error messages and you can then check your server logs to see what, if anything, is getting through your router.

For testing purposes, consider putting the server in the DMZ for a short time and forward all ports to it.  Start from a working configuration and then go backwards.

---

### Post by glacialfury on 2008-11-16
> **cariboo907 said:**
> Are you using a static ip address on your server, or have you set up a long lease for it's dhcp address. The reason being, if you have an ip address on the server that changes occasionally, you will have to change the port forwarding accordingly.

Jim

It is indeed a static IP, assigned as such within the router (in contrast to the lease extension area), and configured manually on the server.

Eventually got it working.  The problem is with the ISP and the router.  Most ports forwarded on the router still ended up not being open, even though they were listed as such.  Port 8080 *was* open, and I configured apache to use that, and the site is now accessible.

Thank you all for the suggestions.

---

