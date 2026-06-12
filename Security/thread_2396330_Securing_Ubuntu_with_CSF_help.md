---
title: "Securing Ubuntu with CSF help"
date: 2018-07-13
forum: Security
---

### Post by goldenpear on 2018-07-13
I am setting up a new server and I am using webmin with CFS so that I can have a nice GUI to manage my firewall.

I want to setup so that I have access on all ports from my home IP address ( I added my IP to csf.ignore)

I want to block access to all ports to all addresses apart from 3 ports, I am not sure how I should set that up. Could someone explain how I can do that can I block all access by putting in 0.0.0.0 and then opening the ports I need ?

Thanks for your help

---

### Post by CharlesA on 2018-07-14
I usually add my firewall rules to csf.allow and limit the ports set in csf.conf to outbound ports (DNS, HTTP, etc).

This might help.. [https://www.digitalocean.com/community/tutorials/how-to-install-and-configure-config-server-firewall-csf-on-ubuntu](https://www.digitalocean.com/community/tutorials/how-to-install-and-configure-config-server-firewall-csf-on-ubuntu)

---

