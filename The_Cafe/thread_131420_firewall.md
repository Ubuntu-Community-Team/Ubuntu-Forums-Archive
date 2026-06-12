---
title: "firewall"
date: 2006-02-16
forum: The Cafe
---

### Post by jxb on 2006-02-16
what firewall do you use or recommend for a small company network? I'm currently searching for a new firewall, I'd prefer an open source solution... if you post links and/or your solution and experience it would be helpful! thanks

---

### Post by rsmereka on 2006-02-16
All Linux's above a certain version can use iptables is a feature that provides a firewall at the kernel level. Iptables support has to be compiled into the kernel. I believe that Ubuntu has this support enabled by default.

The tricky thing with iptables are the rules. You can manage the rules from the command line (the hard way) or using a graphical program like firestarter.

Here is what I just did. I brought up the Synaptic Package Manager (system->administration->synaptic package manager) and did a search for firewall. Unfortunately, firestarter was not on the list but Shoreline Firewall was. From Shortline's website, they start that it is not the easiest but most flexible.

I have used iptables for quite some time and I am very happy with it. I manage the rules the hard way (command line).

---

