---
title: "djbdns help"
date: 2005-10-24
forum: Server Platforms
---

### Post by kevinfreitas on 2005-10-24
Just had a server crash and it took all my config files with it. I'm trying to setup TinyDNS so my server can act as a name server and host for multiple websites and domains. I've had this running and my domain registrar's are all pointed to ns.example.net but I'm not having any luck. Can someone have a look at my TinyDNS data file to tell me if I'm doing things correctly?

```

# the nameserver is running on the same machine as the web server
.example.net:1.2.3.4:ns.example.net:86400

# example.net with a couple of sub-domains
=example.net:1.2.3.4:86400
+www.example.net:1.2.3.4:86400
+some.example.net:1.2.3.4:86400
+another.example.net:1.2.3.4:86400

# example2.org and multiple other domain names =example2.org:1.2.3.4:86400
+www.example2.org:1.2.3.4:86400

```

If someone wants to see my actual data file just let me know -- I can also provide other connectivity info upon request. I really appreciate any help.

Cheers! ~ Kevin

---

### Post by matthurne on 2005-10-24
Call me crazy - but - do you really have the IP address 1.2.3.4?  If not, then your config is obviously not going to work.

---

### Post by kevinfreitas on 2005-10-25
These are just dummy numbers and domains to mimic my TinyDNS data file. I'm just trying to figure out if I've got things right in here. If anyone else has an example of their own data file with description I'd appreciate it.

Cheers!   ~ Kevin

---

### Post by greengeek on 2005-11-01
It seems like your setup there is correct. More likely, tinydns is not responding to queries from the outside world. Make sure that tinydns is running, and check which interface/IP tinydns is bound to. Usually (but not always), tinydns binds to 127.0.0.1, so it only answers queries from the local host. You would also need to run dnscache bound to your actual IP address to answer outside queries, or reconfigure tinydns to bind to an IP address that is accessible from the Internet. Hope that points you in the right direction.

---

