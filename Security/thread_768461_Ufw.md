---
title: "Ufw"
date: 2008-04-26
forum: Security
---

### Post by pzt on 2008-04-26
Hey there. This is a bit blurry on whether it should be under Security or Networking, feel free to kick it elsewhere.

I'm currently setting up my firewall on a remote machine, meaning I'm SSHing to it.

What I want is to have a default deny rule, with an accept on SSH only. Since I am working remote, it would be preferable to set the accept rule before doing the default deny.

My question; if I set an accept on 22 before I do the default deny, will it work?

Guessing it'll be fine, but since I'm not really in a position to go to the machine, certainty is preferred. :)

---

### Post by Monicker on 2008-04-26
Yes, that will work.  You can always verify by doing "sudo iptables -v -L", before implementing the deny rule, which will show you how much traffic hit the existing rules.  

I understand about wanting to be certain.  Once I locked myself out of a router that was several states away.  :o

---

