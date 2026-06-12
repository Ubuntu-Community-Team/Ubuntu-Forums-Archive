---
title: "Reverse NAT to KVM box doesn't work under Natty"
date: 2011-05-16
forum: Virtualisation
---

### Post by kevpatts on 2011-05-16
Hey,

I have a few VMs on my machine and I used to be able to port forward ports from my Dom0 machine to them using the iptables commands (for HTTP traffic):```
sudo iptables -t nat -I PREROUTING -p tcp --dport 80 -j DNAT --to-destination 192.168.122.5:80
kpattison@kpattison-ubuntu:~$ sudo iptables -I FORWARD -m state -d 192.168.122.0/24 --state NEW,RELATED,ESTABLISHED -j ACCEPT
```These commands don't seem to work in Natty. How can I get it working again?

Kevpatts

---

