---
title: "How to create many OpenVPN servers for many clients?"
date: 2014-01-10
forum: Server Platforms
---

### Post by mbnoimi on 2014-01-10
Using [this guide](https://help.ubuntu.com/12.04/serverguide/openvpn.html) I successfully created single OpenVPN server for many clients.

How can I create many OpenVPN servers for many clients each server has own ca.crt and ca.key?

---

### Post by TheFu on 2014-01-10
How can this be done?  Script everything.
 ... or pay someone else to script it for your needs. Use bash, perl, awk, ruby, python ... 

I would think that the openvpn team has tools for this in their commercial offering or will offer consulting services to provide it.

---

### Post by SeijiSensei on 2014-01-10
Have each server run on a separate port.  You can create multiple server definitions and place them in .conf files in /etc/openvpn.  I have a single server to which multiple clients connect using simple shared-key configurations.  Each one connects on a separate port.

---

### Post by TheFu on 2014-01-10
> **SeijiSensei said:**
> Have each server run on a separate port.  You can create multiple server definitions and place them in .conf files in /etc/openvpn.  I have a single server to which multiple clients connect using simple shared-key configurations.  Each one connects on a separate port.

I've had issues connecting to a VPN on any port that wasn't 443 when traveling. Seems that lots of work and hotel connections filter heavily. At a few places they filtered UDP on 443 as well, so be certain to reserve the 443/TCP on the IP for your personal needs.  OTOH, staying above 10,000 in the ports, should be fine for most people coming in from a home ISP connection.

---

### Post by mbnoimi on 2014-01-10
> **SeijiSensei said:**
> Have each server run on a separate port.  You can create multiple server definitions and place them in .conf files in /etc/openvpn.  I have a single server to which multiple clients connect using simple shared-key configurations.  Each one connects on a separate port.

Actually I was using the same way you suggested for years ago but recently I noticed that some users use port listener to discover the working ports for that I want to separate them by using different master key and certificate.

In Windows I did that easily by putting each server's configuration and its master key, certificate and users related files in separate folder then after restart OpenVPN the server will consider each folder as separated server (It creates multi-network connection equal to number of recognized OpenVPN servers). Under Ubuntu this didn't work because OpenVPN create single master key and certificate!

---

### Post by nilla78ro on 2014-01-10
[COLOR=#444444][FONT=sans-serif]The chroot directive allows you to lock the OpenVPN daemon into a so-called chroot jail, where the daemon would not be able to access any part of the host system's filesystem except for the specific directory given as a parameter to the directive. Thinking if you can start in this way multiple deamons[/FONT][/COLOR]

---

### Post by mbnoimi on 2014-01-10
> **nilla78ro said:**
> [COLOR=#444444][FONT=sans-serif]The chroot directive allows you to lock the OpenVPN daemon into a so-called chroot jail, where the daemon would not be able to access any part of the host system's filesystem except for the specific directory given as a parameter to the directive. Thinking if you can start in this way multiple deamons[/FONT][/COLOR]

Thank you for this suggestion but I think it works as a temporarily procedure; The right procedure suppose to work from OpenVPN & Ubuntu side.

---

