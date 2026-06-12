---
title: "Linux System"
date: 2007-08-20
forum: Server Platforms
---

### Post by beckham on 2007-08-20
Hi,  Please tell me What Are The Commands And How Can I Configure My Linux System To Server As A Dynamic Nat. Thanks in advance.

---

### Post by daniel of sarnia on 2007-08-20
Hello you would have better luck posting this in the sever and security section of the forum here [http://ubuntuforums.org/forumdisplay.php?f=7](http://ubuntuforums.org/forumdisplay.php?f=7)

---

### Post by beckham on 2007-09-07
thanks for the suggestion

---

### Post by hikaricore on 2007-09-07
Moved to Servers & Security

---

### Post by steve.horsley on 2007-09-08
I assume you mean that you have an Ubuntu box that has both an internet connection and a local LAN, and you want to do "internet sharing". I also assume that you have the correct IP addressing already configured on both the LAN and the Internet ports.

Both these things need doing with root priviledge. Since the first one doesn't work with sudo, you need a proper root prompt with the command **sudo -i**.
You need to configure your Ubuntu box to do IP forwarding:
**echo 1 > /proc/sys/net/ipv4/ip_forward**
Then configure NAT. Replace eth0 with the interface name for your internet interface in this command:
**iptables --table nat --append POSTROUTING --out-interface eth0 -j MASQUERADE**

Both these should go in a script somewhere to be run at startup, I suppose. I'll try to figure out a nice script an post it later, but not today.

P.S. Here's a nice reference site:
[http://users.telenet.be/mydotcom/howto/lanconnect/router/linux.htm](http://users.telenet.be/mydotcom/howto/lanconnect/router/linux.htm)

---

