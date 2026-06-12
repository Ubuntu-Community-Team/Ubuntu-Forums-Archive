---
title: "ssh keystroke problems"
date: 2009-10-24
forum: Server Platforms
---

### Post by mrdaze0 on 2009-10-24
I have an issue that I cant seem to find any answers to online when searching.
I am running 9.04 server with OpenSSH_5.1p1 when i connect to the server from my house i have very slow response times after logging in ~1 second until keystroke appears.
Both internet connections are high speed the servers connection is 3Mbps or faster and my home connection is 8Mbps or faster system at house is Mac osx 10.5.8 OpenSSH_5.1p1. 

Any suggestions to increasing response time when typing commands or working in vim?

---

### Post by windependence on 2009-10-24
The fix is to either add the IP address to /etc/hosts, or modify your sshd_config file and set UseDNS to no

On the machine being connected to (remote side/server side)

/etc/ssh/sshd_config

UseDNS no

if the remote side is another linux, then /etc/ssh/ssh_config
in the host * section

CheckHostIP no

-Tim

---

