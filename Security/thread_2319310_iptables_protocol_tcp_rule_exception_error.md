---
title: "iptables protocol tcp rule exception error"
date: 2016-04-02
forum: Security
---

### Post by HardTrickySecurity on 2016-04-02
iptables -A INPUT -m conntrack ! --ctstate ESTABLISHED,RELATED ! -i eth0 -p tcp -m tcp ! --sport 443 ! -s 46.239.117.180 ! -d 192.168.1.2 -j DROP


I am trying to put ! symbol (exception) in -p tcp like this ! -p tcp but it returns the following error:


iptables: Invalid argument. Run `dmesg' for more information.


[ 1801.206571] x_tables: ip_tables: tcp match: only valid for protocol 6 (I am using ipv4)




Is there some kind of workaround to this specific scenario or is just not possible?

---

### Post by SeijiSensei on 2016-04-03
I think you would need to write separate rules for "-p udp" and "-p icmp" if you wish to support that as well.

---

