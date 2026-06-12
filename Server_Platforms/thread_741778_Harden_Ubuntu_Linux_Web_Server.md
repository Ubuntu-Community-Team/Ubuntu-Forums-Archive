---
title: "Harden Ubuntu Linux Web Server"
date: 2008-04-01
forum: Server Platforms
---

### Post by njparton on 2008-04-01
webmin is good but also install openssh-server and then an ssh client from where you'll be administering from (e.g. putty for windows).  That will give you quick and easy access to the command line.

---

### Post by njparton on 2008-04-01
Another thought - start doing some reading on iptables the inbuilt linux firewall and the various GUI's to administer it such as firestarter etc.  I've never quite got to grips with it myself :(

---

### Post by Oldsoldier2003 on 2008-04-01
> **njparton said:**
> Another thought - start doing some reading on iptables the inbuilt linux firewall and the various GUI's to administer it such as firestarter etc.  I've never quite got to grips with it myself :(

bastille is good too. it can be used to harden your server and also get a nice start on your iptables setup. you also should instal DenyHosts to protect your SSH from brute force attacks

---

