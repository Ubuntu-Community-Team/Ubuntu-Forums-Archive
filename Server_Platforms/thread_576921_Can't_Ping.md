---
title: "Can't Ping"
date: 2007-10-15
forum: Server Platforms
---

### Post by dacool25 on 2007-10-15
For some reason I cannot ping my server.  All of my pages are up and apache is working.

I was wondering could IPTABLES be blocking it?  If so, i did try unblocking it but could of had the wrong command.  

Thanks for your help in advance.

---

### Post by codmate on 2007-10-16
Try these IPtables rules:
-A INPUT -p icmp -j ACCEPT 
-A OUTPUT -p icmp -j ACCEPT

---

### Post by dacool25 on 2007-10-16
Still nothing.

The exact code i used was:
```
iptables -A INPUT -p icmp -j ACCEPT
iptables -A OUTPUT -p icmp -j ACCEPT
```

---

### Post by conjur3r on 2007-10-16
Where is your server?  On your LAN, or hosted somewhere else?

Check the firewall logs somewhere in /var/log to see if any ICMP packets are being denied.

---

### Post by dacool25 on 2007-10-16
The server is on my LAN, i'll check the logs tonight when I get home

---

