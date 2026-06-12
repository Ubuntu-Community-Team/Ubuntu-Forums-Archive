---
title: "Apt-Get with Firewall"
date: 2007-08-23
forum: Server Platforms
---

### Post by quartersmile on 2007-08-23
I installed Ubuntu server on an old computer to learn a bit about running a linux server.  Don't have much experience with setting up Linux and I've been following some tutorials I found in trying to set up a secure basic system.

My problem:  after I installed shorewall as a firewall, apt-get doesn't work.  I get an error message: "temporary failure resolving 'archive.ubuntu.com'"  If I stop shorewall, apt-get works.

Following suggestions I found searching the web, I've added the following rules to shorewall:

ACCEPT net fw tcp 80
ACCEPT fw net tcp 80
ACCEPT fw net tcp 53
ACCEPT fw net udp 53

I've read that apt-get runs through port 80, but I haven't been able to crack this nut nor find an answer on the web or these forums.

Can anyone point me to a solution for allowing apt-get through the firewall?

tia,
q

---

### Post by bodhi.zazen on 2007-08-23
See if this link helps :

[http://www.debianhelp.co.uk/shorewall.htm](http://www.debianhelp.co.uk/shorewall.htm)

---

### Post by a9k on 2007-08-23
"temporary failure resolving 'archive.ubuntu.com'" indicated a DNS failure.
Try this command: 'host archive.ubuntu.com'
It should return several addresses. If that fails then you have a problem with DNS lookups (port 53) on your firewall.

---

