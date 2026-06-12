---
title: "VPN -- initialize on startup ..."
date: 2008-07-11
forum: Server Platforms
---

### Post by cwmoser on 2008-07-11
In order to make my VPN (pptpd) work properly, I need to run the following:

# echo 1 > /proc/sys/net/ipv4/ip_forward

Without this, when I establish a VPN to my Server, I can only access or ping the server -- not the other devices on my network.  One I run the above, then I can access all devices on my network.

What is the best way to make this run on boot up?


Carl

---

