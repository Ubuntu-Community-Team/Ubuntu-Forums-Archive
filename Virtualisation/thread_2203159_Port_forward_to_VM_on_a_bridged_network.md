---
title: "Port forward to VM on a bridged network"
date: 2014-02-01
forum: Virtualisation
---

### Post by bewareofthephog on 2014-02-01
Hi all!  I have a CentOS VM running in VirtualBox.  I need to forward a port to it so I can view some software I installed via the web UI.

The host IP is 192.168.1.100

And I have 22 forwarded to this and can connect remotly fine.

The guest is on port 7000 and I have my router forwarding to the guest IP.  In this case 192.168.1.101

My question is...do I need to forward 7000 to the host and then forward from there?  Or can I direct my router to forward directly to the guest IP?

Edit:
I should have mentioned the host os is Ubuntu 13.10 otherwise I wouldn't be asking here ;)

---

### Post by TheFu on 2014-02-02
Using a bridged network - just treat it like any other real machine. i.e. forget that there is a host.

---

