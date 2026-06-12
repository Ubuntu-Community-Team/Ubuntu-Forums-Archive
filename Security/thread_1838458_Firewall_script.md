---
title: "Firewall script"
date: 2011-09-03
forum: Security
---

### Post by zedixal on 2011-09-03
Hi,

last week a friend set up for me a Lubuntu machine, with a firewall script located in /usr/local/sbin and activated by a directive in /etc/network/interfaces:

auto provider
iface provider inet ppp
    pre-up /usr/local/sbin/firewall start
    pre-up /sbin/ip link set dev eth0 up
    provider dsl-provider
    post-down /sbin/ip link set dev eth0 down

I enclose the script [here]("http://pastebin.com/6UzNvraL").

I'm not a iptables expert, but many lines seem redundant (see drop_rules :confused:). Being accustomed to firestarter, I'd like to know if:

1) this script is safe/functional
2) it is simply too bloated for my humble needs (e.g. web surfing, email, ftp)


Thank you

---

### Post by bodhi.zazen on 2011-09-03
The default configuration tool for Ubuntu is ufw

```
sudo ufw enable
``` is sufficient, if not overkill, for 99.999 % of Desktop users.

---

### Post by zedixal on 2011-09-04
OK, I'll *DROP* :P that ugly script and enable ufw

---

### Post by kerry_s on 2011-09-04
> **zedixal said:**
> OK, I'll *DROP* :P that ugly script and enable ufw

you can install gufw if you want a gui for that.

---

### Post by zedixal on 2011-09-05
Just installed gufw,

set Incoming and Outgoing to Deny,

and opened outgoing udp port 53, tcp ports 80, 443, 110 and 25

I've checked the settings with some online firewall testers (GRC, etc.) and it works great!

(If I will need FTP I'll take same risk - lol - and set Outgoing to Allow)

Thank you all

---

