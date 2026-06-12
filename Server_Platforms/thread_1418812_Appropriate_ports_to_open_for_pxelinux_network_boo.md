---
title: "Appropriate ports to open for pxelinux network boot server?"
date: 2010-03-01
forum: Server Platforms
---

### Post by nerr on 2010-03-01
Hello again, I set up a PXE network boot server today which is able to push down a LiveCD image to any PC in the house that is able to boot via PXE.  It works quite well, but only when I flush my iptables rules completely, which leads me to suspect that I'm missing a port or two which must be opened to allow PXE booting.  Right now, I have the following ports open which seem to be related to DHCP/TFTP/PXE:

UDP 67, 68, 69, 4011

Am I missing any ports here?  After doing some diagnostic testing, it seems that whenever a client is attempting to boot with the firewall rules in place, a random TCP port between 700 and 1000 receives requests, but is unable to fulfill these as the firewall stops them from passing.  I would rather not blindly open 300 ports if possible, so any insight to this situation would be appreciated.

---

### Post by stlsaint on 2010-03-01
seems to be port 67, 
[http://en.wikipedia.org/wiki/Preboot_Execution_Environment#Protocol](http://en.wikipedia.org/wiki/Preboot_Execution_Environment#Protocol)

---

### Post by nerr on 2010-03-01
67/UDP is allowed through the firewall, and the problem still exists.  Any other thoughts?

---

### Post by koenn on 2010-03-01
a pxe boot client will talk to ports 67 and 69 of your server, while sending from (and expecting to receive on) some random port, so your firewall needs to allow your server to talk *from* udp ports 67,69 *to* a random port at the client. Does your firewall allow that ? (allowing "RELATED" and "ESTABLISHED" might be enough, but as udp is stateless, it may be better to explicitely allow those source ports)

---

