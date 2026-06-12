---
title: "BIND9 server    ping slow by hostname fast by IP"
date: 2007-08-17
forum: Server Platforms
---

### Post by dizzaniix on 2007-08-17
Ok, I will try my best at describing this. I have a Ubuntu 7.04server running bind9. Bind is working and resolving, but when I try to ping a host that this bind server handles it pings super slow...but if i ping by IP address to the same host its fast. 



Any ideas?

---

### Post by dizzaniix on 2007-08-17
i fixed it...i disabled ipv6

---

### Post by none-letmebe on 2008-02-27
How did you disable ip6?
I have a similar problem, which led me to reinstall at first.
If I ping yahoo.com (or anyother FQDN) ICMP returns on request every 2 second but the actual time to respond as reported by ping is very fast.  When I ping the IP address its as fast as usual.

---

### Post by none-letmebe on 2008-02-27
Found it :
1. IPv6 is supported by default in Ubuntu and can sometimes cause problems.
2. To disable it, open a Terminal (Applications > Accessories > Terminal) and type the command: gksudo gedit /etc/modprobe.d/aliases.
3. Find the line alias net-pf-10 ipv6 and change it to read alias net-pf-10 off.
4. Reboot Ubuntu.

Will try this evening.

---

