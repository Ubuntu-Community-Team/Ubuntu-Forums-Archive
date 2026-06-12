---
title: "Problem accessing my webserver"
date: 2010-04-20
forum: Security
---

### Post by RegUB on 2010-04-20
I am running Apache webserver on my Ubuntu system to allow me to develop Web applications on my home (wireless) network. For some reason, when I attempt to access my Webserver using the Ubuntu system's LAN IP address (from my laptop, typing the IP address into Firefox), it no longer works - I get "The connection was refused when attempting to contact...Though the site seems valid, the browser was unable to establish a connection." . I can ping the Ubuntu server's IP address from the laptop, but it won't allow the connection.

The same thing happens when I try this from Firefox on the Ubuntu server itself - it works OK if I use 'Localhost', but not if I use the server's own IP address. So I think it's a Linux security issue rather than an Apache configuration issue - it doesn't seem to get as far as Apache.

This used to work OK. Any idea what could be causing the connection to be blocked?

---

### Post by LeeDaugherty on 2010-04-20
Hard to troubleshoot without more information.  If Apache is running on 127.0.0
.1 that would explain it, as this is a local address and not public, netstat -tunlap and look at where apache is listening.  Are you running any firewall/iptables scripts?

---

### Post by RegUB on 2010-04-20
Thanks, it was only listening on the localhost address - so it was an Apache issue after all! It's been a while since I did anything with Apache, I think I must have set it to use the local host address some months ago and forgotten about it.

---

