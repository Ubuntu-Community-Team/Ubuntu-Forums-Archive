---
title: "iptables to protect my VPS"
date: 2016-07-26
forum: Security
---

### Post by atux on 2016-07-26
Hi. i do have a VPS with a public IP (eg  62.45.60.100) and i would like to protect it with iptables. The system has the ssh at port 32322 and it runs OPENVPN at port 1194. at the moment i have only a basic set of iptables and i would like to expand it to make my system fail proof. all services from inside of the system to be allowed. from outside world allow only ssh at port 32322 and openvpn at port 1194. also all users connected through openvpn to be able to browse the net. The iptables at the moment are saved with /etc/init.d/iptables-persistent save

---

### Post by TheFu on 2016-07-26
"Fail proof?"  What does that mean? Nothing is fail proof and firewalls are just 1 layer of system security.

The best way to handle firewalls is to block everything except the specific IPs where you will come in from. If your IPs aren't static, then you can't do that.

For simple rules like you need, probably should just use ufw with a default deny rule. ufw is an easy interface into netfilter (the Linux firewall). Also, don't VPS providers give console access, so if you lock yourself out with firewalls, then you can come in through the console and fix it?

I've seen where some people, while testing new firewall rules, will setup a 5 min time out and remove the restrictive rules after that time ... just in case.

Don't forget to block the internal network at the VPS. Your VPS neighbors might not be nice people.

[https://wiki.ubuntu.com/BasicSecurity](https://wiki.ubuntu.com/BasicSecurity) is a place to start with the other layers. Debian has a security guide which is apropos too.

---

### Post by QIII on 2016-07-26
Just as a general rule, when thinking of security never let ideas like "fail proof", "fool proof" or "I'm done" enter into your mind.

---

### Post by atux on 2016-07-27
Hi. thanks a lot for your replies. i know that fail proof and similar expressions are the same as 'this is all i thought of'.
i do not have static IPs. the vps in case i am locked out i can get a console from the provider. is there a way to have the full set of iptables to allow ssh and openvpn only, please? all outbound services from the VPS to be unrestricted. all the opevn connections be able to access the internet from within the VPS. drop and block scanners. blacklist for 24 hours failed ssh attempts (<3/hour).

---

### Post by TheFu on 2016-07-27
Just set the default rule to DENY and open ssh (22/tcp) and openvpn (usually udp) open to the world. Install fail2ban and ssh failures will get dynamically added. Configure how long the failed IP sources are blocked in the /etc/fail2ban/ config files.  That would leave outbound open (which isn't exactly secure).

fail2ban will need to be manually configured for openvpn. I don't bother. Nobody attacks key-based VPN ports, IME.  Plus, I use ssh for almost everything. [http://blog.jdpfu.com/2014/09/23/you-don-t-know-ssh-about-ssh](http://blog.jdpfu.com/2014/09/23/you-don-t-know-ssh-about-ssh)

Google can find the specific rules you seek, but if you have a default DENY rule, there isn't any reason to deal with scanners.  [https://help.ubuntu.com/community/UFW](https://help.ubuntu.com/community/UFW) should be enough.

---

