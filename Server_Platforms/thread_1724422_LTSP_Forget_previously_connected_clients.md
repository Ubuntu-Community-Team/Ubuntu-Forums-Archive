---
title: "LTSP: Forget previously connected clients"
date: 2011-04-08
forum: Server Platforms
---

### Post by skinney on 2011-04-08
Hi!

I've set up an ltsp-server that boots up clients and makes them run rdesktop to remotely connect to a windows server. Now, I'm having a problem where every client I connect to the server get's its own IP-adress, as if the LTSP-server remembers each client somehow.

Example: Everytime i connect client A, it gets the ip-adress 192.168.0.24, even though 192.168.0.20-23 are available. What I want is for the client to grap the first available ip-address, instead of getting the same ip everytime it boots.

Can this be done?

---

