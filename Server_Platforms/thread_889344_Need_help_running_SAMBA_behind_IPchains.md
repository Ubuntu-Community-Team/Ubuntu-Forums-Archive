---
title: "Need help running SAMBA behind IPchains"
date: 2008-08-14
forum: Server Platforms
---

### Post by tdcdodger on 2008-08-14
I have just set up an ubuntu server box using ipchains as its firewall. However, while implementing the firewall, I "broke" the connectivity of the SAMBA service that resides behind it.

I am wondering what ports (both TCP and UDP) are neccessary to ACCEPT in order to connect to a samba share (any copy/browse files of-course).

As of right now, my ipchain script looks like this:
```
#clear iptables
iptables -F

#blanket Security
iptables -P INPUT DROP
iptables -P OUTPUT DROP

#ssh
iptables -A INPUT -p tcp --destination-port ssh -j ACCEPT
iptables -A OUTPUT -p tcp --source-port ssh -j ACCEPT

#http
iptables -A INPUT -p tcp --destination-port http -j ACCEPT
iptables -A OUTPUT -p tcp --source-port http -j ACCEPT

#samba(limited to connections from *REMOTE IP*)
iptables -A INPUT -p tcp -s *REMOTE IP* --destination-port 137:139 -j ACCEPT
iptables -A OUTPUT -p tcp -d *REMOTE IP* --source-port 137:139 -j ACCEPT
```

The http and ssh work fine, but I cannot find the correct combination of ports to ACCEPT for SAMBA anywhere. Thanks in advance.

---

### Post by ibutho on 2008-08-14
Try the foloowing ports: 135 137 138 139 and 445.

---

### Post by tdcdodger on 2008-08-14
bump

Thank you very much for your response. I tried to ACCEPT the ports that you listed as both udp and tcp, but still no luck. Does anyone else have any suggestions?

---

### Post by MJN on 2008-08-14
Post your latest ruleset as chances are you've just made an error adding the new rules.

Mathew

---

