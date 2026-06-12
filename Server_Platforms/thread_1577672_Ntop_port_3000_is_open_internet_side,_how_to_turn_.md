---
title: "Ntop port 3000 is open internet side, how to turn off internet access."
date: 2010-09-19
forum: Server Platforms
---

### Post by MechaMechanism on 2010-09-19
I installed Ntop.  Port 3000 is shown as open by web port scanners.  How to turn off internet access so that the port is closed to the internet.  I only need localhost access.

---

### Post by koenn on 2010-09-19
tell ntop not to listen on your internet interface (look up the options -i or --interface in man ntop)

alternatively, block internet access to port 3000 by means of a firewall. iptables could do that.

---

### Post by LightningCrash on 2010-09-19
check the file /etc/default/ntop

there are likely config options in there that do what you want

---

### Post by MechaMechanism on 2010-09-19
I changed Ntop web server to 127.0.0.1:3000 and that solved it.  The interface option controls what interface to capture on.  I got confused between the two, I kept changing the interface for the network capture.  Thats what you get for trying to setup Ntop at 4 AM.

---

### Post by koenn on 2010-09-19
oh, ok.
I guess I wasn't paying attention ether :)

---

