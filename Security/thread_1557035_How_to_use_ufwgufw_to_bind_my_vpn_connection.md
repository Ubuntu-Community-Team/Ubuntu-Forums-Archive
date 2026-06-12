---
title: "How to use ufw/gufw to bind my vpn connection?"
date: 2010-08-20
forum: Security
---

### Post by dogdo on 2010-08-20
Is there a way to use the firewall to essentially lock certain programs like firefox and transmission to my vpn connection-so that in the event that my  vpn connection goes down these programs do not use my default ISP Internet connection.

---

### Post by bodhi.zazen on 2010-08-20
Not easily.

Your best bet is to use iptables, with a set of rules, save the rules iptables-save, and then call the rules in your networking scripts, /etc/networking/interfaces with pre-up / post up and pre/post down commands.

---

