---
title: "irc!"
date: 2008-06-29
forum: Server Platforms
---

### Post by 0perator on 2008-06-29
i set up an irc server on my ubuntu machine..

i can do /server localhost

and it works fine

but when i try and do /server uberbeef.org it says

* Looking up uberbeef.org
* Connecting to uberbeef.org (86.150.246.184) port 6667...
* Connection failed. Error: Connection refused
* Disconnected ().

uberbeef is configured to point to my machine..

please help

---

### Post by mrpeenut24 on 2008-06-29
Is your router/firewall set up correctly to allow/forward the necessary ports?  It looks like it's going out and then coming back in.  If it works with localhost, then that's likely the problem.

---

