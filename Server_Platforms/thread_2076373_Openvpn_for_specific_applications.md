---
title: "Openvpn for specific applications"
date: 2012-10-25
forum: Server Platforms
---

### Post by sinplomo on 2012-10-25
Hi

Is there any way to make specific applications going through a VPN while the others app don't?

---

### Post by chadk5utc on 2012-10-31
I would consider routing/port forwarding with iptables

---

### Post by SeijiSensei on 2012-11-02
You could simply tell the application to use a VPN-only IP address as its target.  An easy way to do this is to create an entry in /etc/hosts that points to the remote VPN address.  Then tell the application to use that hostname.

---

### Post by HermanAB on 2012-11-03
Howdy,

You could also run an application as a specific group, then set up an iptables rule to trigger on that group.

There is an example here:
[http://www.aeronetworks.ca/howtos/skype-ssh-tunnel-howto.html](http://www.aeronetworks.ca/howtos/skype-ssh-tunnel-howto.html)

---

