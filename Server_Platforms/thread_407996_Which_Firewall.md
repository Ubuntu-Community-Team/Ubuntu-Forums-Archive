---
title: "Which Firewall"
date: 2007-04-12
forum: Server Platforms
---

### Post by duncansid on 2007-04-12
Hi All,
A couple of months ago I set up ubuntu for the 1st time taking advice and instructions from a idiots guide on a web page. The server has run perfectly and is locked down well but I now need to open up ftp access from the local network to a few ip addresses. The problem I have is that I can't remember which firewall I used. I've checked the iptables using iptables -L and they are empty. Any sugestions?

Thanks in advance.

---

### Post by BitHosts on 2007-04-12
Personal Fav - Shorewall (configuration interface for iptables) very easy to set up and very effective. Check to see if its installed in /etc/shorewall

---

### Post by duncansid on 2007-04-13
Thanks but it is not shorewall any other suggestions please I don't want to have to format and start again

---

### Post by Rush_898 on 2007-04-13
I'm pretty much a newb myself but is it possibly Firestarter?  I have used this frontend to ipchains before and it seems fairly common.  Is this a box w/ a GUI?  If so I believe you can browse the list of installed packages in synaptec.  If not try maybe, cat /var/install.log

---

### Post by bapoumba on 2007-04-13
firestarter ? (which is basically a gui to iptables).

---

