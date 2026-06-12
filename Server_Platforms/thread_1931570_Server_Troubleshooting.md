---
title: "Server Troubleshooting"
date: 2012-02-25
forum: Server Platforms
---

### Post by paulwilson5x on 2012-02-25
First time user of ubuntu. Running ubuntu desktop 11.10 and server 11.10 in virtual box. Server was serving my webpages to desktop client, but now has stopped. How can I troublshoot this?

---

### Post by Porcini M. on 2012-02-25
Is the server still connected to the network? Type "ifconfig" in a terminal on the server & see what it says. If it looks like it's connected, is apache still running?

---

### Post by kevinthecomputerguy on 2012-02-26
Is it running in Bridge or NAT.

Webserver will need bridge to serve to same network as host(s) and that network will need DHCP

---

### Post by paulwilson5x on 2012-02-26
if config looks ok, i have tried bridged network on the server with dhcp, still not working

---

### Post by paulwilson5x on 2012-02-26
server is connected to internet but not the desktop

---

### Post by paulwilson5x on 2012-02-26
can any1 help?

---

