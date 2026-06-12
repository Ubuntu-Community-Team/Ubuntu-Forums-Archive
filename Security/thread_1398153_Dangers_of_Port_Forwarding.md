---
title: "Dangers of Port Forwarding"
date: 2010-02-04
forum: Security
---

### Post by RichardCL on 2010-02-04
Dear Forum,

Up to now I've been playing with Ubuntu whilst storing important data elsewhere for about 2 years. Now I'm ready to move to Ubuntu completely but want to address my security.

I'm currently using a desktop and server behind a hardware firewall / Internet router. The router has DynDNS and forwards port 80 to the webserver and a port I picked at random to the desktop 22 for SSH with private keys. SSH passwords are disabled.

The first question is, is there a danger of running different security levels on the two machines? I don't care about the server, there is no data on it so I currently forward port 80 and am considering forwarding ports 631 (CUPS) and a port for LDAP. Will this effect my desktop (which has info I don't want to loose).

The next question is whether port forwarding / hardware firewall is actually a safeguard against attack.

Many thanks in advance for your help.


Richard

---

### Post by CharlesA on 2010-02-04
Considering that you can usually only do port forwarding to one IP, it shouldn't be a problem.

---

### Post by warriorforgod on 2010-02-04
Anytime you open up ports to the outside world, you are opening up a possible hole for an attacker.  What kind of hardware firewall are you using?  Is it something simple like a linksys router, or is it a full blown firewall device?  If the second is correct, I would suggest running some kind of IPS, and you can also run an IDS on your desktop/server.  Sounds like you locked down SSH pretty well so that is good.  That would probably be the most common attack vector.

---

### Post by tgalati4 on 2010-02-04
I would only open the ssh port when you really need to use it.  If you use it every day, then a random port provides some "security by obscurity".

Of course allowing remote administration of your router is even more risky, so you need to think your security strategy before leaving ports open 24-7.

---

