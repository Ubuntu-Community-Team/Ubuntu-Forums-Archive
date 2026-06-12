---
title: "Dynamic L2L IPSEC to Cisco IOS"
date: 2012-01-30
forum: Security
---

### Post by martinbuffleo on 2012-01-30
I need to build a Linux box that will act as a gateway/VPN endpoint to allow me to run a Site to site/ LAN to LAN VPN to My Headoffice which ahs a Cisco IOS VPN endpoint.
 
I need the Linux box to be happy with any public IP address it has.
 
Can this be done.
 
I'm looking at Racoon but I have installed IPSEC tools and still dont see a racoon.conf file to configure.

---

### Post by movieman on 2012-01-30
I think it's under /etc/racoon?

Note that IPSEC is insanely difficult to configure, as there's usually one way to configure it correctly and a trillion billion bazillion ways to configure it wrong. You can tell it was designed by a committee who wanted to throw the kitchen sink in there.

---

