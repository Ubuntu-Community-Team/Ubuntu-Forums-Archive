---
title: "2 firewalls? for Ubuntu and XP"
date: 2009-02-22
forum: Virtualisation
---

### Post by Arminius on 2009-02-22
I'm running ubuntu and using vmware workstation to run windows xp home, and I'm using the internet on both of them, so do I need just one firewall on the ubunutu side, or does xp also need it's own firewall?

---

### Post by HermanAB on 2009-02-23
As usual, it depends on your setup.  You can configure a guest either with a bridge and its own public IP address, in which case you need a firewall on the guest too, or you can set it up with NAT, using a private non-routable 192.168.x.y IP address on the virtual LAN, in which case only the host needs a firewall with some ports forwarded to the guest.

Hope that helps!

Herman

---

### Post by bodhi.zazen on 2009-02-23
What is you want a firewall to do for you ?

---

