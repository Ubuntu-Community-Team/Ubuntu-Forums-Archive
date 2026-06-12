---
title: "Firewall for new server"
date: 2009-10-17
forum: Security
---

### Post by Asheguy79 on 2009-10-17
I am about to set up my first server using LAMP and I am new to this so what is a good firewall to use.  I am using the desktop version with taskel due to this is the only computer I own right now but I need the server for my rails developments.  Will fire starter be enough or should I use ufw.  I have also read about pfSense  in Linux User & Developer would this one work?  Any advice, knowledge, or websites to go to would be great.

---

### Post by CharlesA on 2009-10-17
I've always used iptables. It's included in ubuntu by default.

---

### Post by cariboo on 2009-10-17
The preferred tool for setting firewall rules is ufw, which is installed by default, if you need a gui tool, install gufw, it is in the repositories.

---

### Post by Lars Noodén on 2009-10-19
[INDENT]   "*ufw  is not intended to provide complete firewall functionality via its command interface, but instead provides an easy way to add or remove simple  rules.  It is currently mainly used for host-based firewalls.*"
[http://manpages.ubuntu.com/manpages/karmic/en/man8/ufw.8.html](http://manpages.ubuntu.com/manpages/karmic/en/man8/ufw.8.html)
[/INDENT]

UFW is a front-end for IP Tables, you can safely start with that.  Later, if you pursue filters, you can learn to write scripts for IP Tables. 

gufw is a nice graphical front end for UFW (which is a front-end for IP Tables) written in python.  FWBuilder is also highly thought of.  My ownpreference is to use IP Tables via shell script.

pfsense is a system-in-a-ramdisk using BSD.  You'd need a separate machine for it to run on.  It fills the same niche as OpenWRT, Tomato or Quagga.  You could make your own using busybox and iptables.

---

### Post by sh4d0w808 on 2009-10-20
Maybe [this page]("http://easyfwgen.morizot.net/gen/") can also help U. After generating the iptables script, it is well commented.

---

