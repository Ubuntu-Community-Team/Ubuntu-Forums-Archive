---
title: "Squid Proxy Config Help"
date: 2011-11-09
forum: Server Platforms
---

### Post by acoustix on 2011-11-09
I'm attempting to run an Ubuntu server (10.04) with Squid3 installed and a public IP address.  I have a fleet of wireless devices that will be outside of my companies network - using free Wi-Fi.  I want to force these devices to use a proxy server that will only allow access to certain domains/IP addresses.  Basically it will be a web filter.

How can I configure Squid to only allow access to these predetermined sites?  

Thanks!
-Nick

---

### Post by vasile002 on 2011-11-09
you can either use dansguardian or just block everything except what you need using iptables

---

### Post by acoustix on 2011-11-09
Ok.  I'm pretty new to Linux and I'll need a little more guidance.

---

