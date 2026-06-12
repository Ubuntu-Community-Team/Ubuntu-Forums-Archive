---
title: "Restricted Ports"
date: 2005-08-07
forum: Server Platforms
---

### Post by ph8 on 2005-08-07
Does anyone know a way for normal users to bind to port 80 without using sudo?

---

### Post by adeh on 2005-08-10
You can't. The linux kernel is set to restrict access to ports below 1024 for root prcesses only. This is a good security measure, but it can make life a little more complicated. There may be other ways to solve this problem, but what I did was add some records to the internal routing table so that restricted ports get redirected to unrestricted ports. That way, I can run the processes using restricted users, and the computer is safer. Of course, I am far from a security expert, so maybe someone else can elaborate on the whole process.

Here is the code I added to /etc/network/interfaces

# configure the port redirection that allows Tomcat to run as non-root
up /sbin/iptables -t nat -F
up /sbin/iptables -t nat -A PREROUTING -p tcp --dport 443 -j REDIRECT --to-ports 8443
# you could change your config to route 80 to the port of your choice.

I posted this in another thread, but can't seem to find it now.

Good luck.

---

### Post by HumanAnarchist on 2006-07-17
Thanks for this. You saved my day :) /me hands you 1000 karma points

---

