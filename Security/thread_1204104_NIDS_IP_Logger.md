---
title: "NIDS IP Logger"
date: 2009-07-04
forum: Security
---

### Post by Aiman on 2009-07-04
I never used a NIDS on Debian or Ubuntu before, my network security is based on IPtables and sysctl.conf. i tried Ubuntu 8.10 and 9.04 but i still think 8.04 is stable enough and works great.

When i was using Windows, i had Norton Personal firewall 2004 for one reason, it had a function that logs attacks ( Attacker IP address and even geographically locate the IP )

I was wondering if there is such a tool on Ubuntu or Debian like operating systems, I'm pretty sure attacks are preformed or scans, it would be nice to know whos doing such scans/attacks.

So my question is, any recommendation about such applications ?

---

### Post by cariboo on 2009-07-04
Basically any service that needs a login is logged in /var/log/auth.log, so you can check the log file to see what is happening. THis assumes you are directly connected to the internet, and not through a router. 

If you are connected through a router and don't have any ports forwarded, you have nothing to worry about. 

If you have port forwarding enabled, I would suggest you use denyhosts to allow attackers a maximum of 5 tries before the ip is banned. You can set the length  of ban time, as well as the number of tries in the configuration file. Denyhosts is in the repositories.

---

### Post by Aiman on 2009-07-04
I've checked DenyHosts and read about it before, it helps when they try to brute force attack you.
but the thing im looking for is something that will log scans.
i remember having logs back when my own ISP used to scan their user, they preform port scans on their own customers. and it was nice calling them with all the info and throwing it in their faces.

---

### Post by rookcifer on 2009-07-04
If you're using iptables locally then psad will do what you want.

---

### Post by Aiman on 2009-07-05
from the information on the psad main page, it sounds like its the thing im looking for
ill give it a try and report back

---

### Post by Aiman on 2009-07-05
I had PSAD setup, but i'm not 100% sure about the rules
the iptables rules i have set

> #!/bin/bash
[ "${METHOD}" != loopback ] || exit 0
/sbin/iptables -A INPUT -i eth0 -p tcp --dport 22 -m state --state NEW -m recent --set --name SSH
/sbin/iptables -A INPUT -i eth0 -p tcp --dport 22 -m state --state NEW -m recent --update --seconds 60 --hitcount 4 --rttl --name SSH -j DROP
/sbin/iptables -A INPUT -m iprange --src-range 193.188.116.129-193.188.116.134 -j DROP
/sbin/iptables -A INPUT -m iprange --src-range 193.188.115.000-193.188.115.255 -j DROP
/sbin/iptables -A INPUT -m iprange --src-range 193.188.117.160-193.188.117.191 -j DROP
/sbin/iptables -A INPUT -m iprange --src-range 193.188.108.000-193.188.108.127 -j DROP
/sbin/iptables -A INPUT -p tcp –syn –dport 25 -j ACCEPT
/sbin/iptables -A INPUT -p tcp –syn -m limit –limit 1/s –limit-burst 4 -j ACCEPT
/sbin/iptables -A INPUT -p tcp –syn -j DROP
/sbin/iptables -N port-scan
/sbin/iptables -A port-scan -p tcp --tcp-flags SYN,ACK,FIN,RST RST -m limit --limit 1/s -j RETURN
/sbin/iptables -A port-scan -j DROP
/sbin/iptables -A specific-rule-set -p tcp --syn -j syn-flood
/sbin/iptables -A specific-rule-set -p tcp --tcp-flags SYN,ACK,FIN,RST RST -j port-scan
/sbin/iptables -A INPUT -p tcp -i eth0 –dport 137:139 -j REJECT
/sbin/iptables -A INPUT -p udp -i eth0 –dport 137:139 -j REJECT
/sbin/iptables -A INPUT -j LOG
/sbin/iptables -A FORWARD -j LOG
/sbin/iptables -A INPUT -j DROP

i did a full port scan using grc.com, but PSAD didn't report anything
and i used nmap-online scan, still PSAD didn't report or log anything when i checked psad -S
the whole idea behind what i was doing is knowing when im being scanned

---

### Post by Aiman on 2009-07-08
So i got psad running with a new set of rules for the iptables
ive uploaded both files if some one needs them, had to remove some comments from the psad file to get the right size

thanks for the help


[ATTACH]120360[/ATTACH]

[ATTACH]120361[/ATTACH]

---

