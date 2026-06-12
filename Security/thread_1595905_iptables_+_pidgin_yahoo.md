---
title: "iptables + pidgin yahoo"
date: 2010-10-13
forum: Security
---

### Post by tad1073 on 2010-10-13
When I ad -A INPUT -j DROP or -P INPUT DROP pidgin freezes using the yahoo protocol. Any help would be greatly appreciated. 

My iptable rules are listed below.

```
-A INPUT -m conntrack --ctstate RELATED,ESTABLISHED -j ACCEPT 
-A INPUT -p tcp -m tcp --dport 80 -j ACCEPT
-A INPUT -s 192.168.1.0/29 -p tcp -m tcp --dport 111 -j ACCEPT 
-A INPUT -s 192.168.1.0/29 -p udp -m udp --dport 111 -j ACCEPT 
-A INPUT -s 192.168.1.0/29 -p udp -m udp --dport 2049 -j ACCEPT 
-A INPUT -s 192.168.1.0/29 -p tcp -m tcp --dport 2049 -j ACCEPT 
-A INPUT -s 192.168.1.0/29 -p udp -m udp --dport 137 -j ACCEPT 
-A INPUT -s 192.168.1.0/29 -p udp -m udp --dport 138 -j ACCEPT 
-A INPUT -s 192.168.1.0/29 -p tcp -m state --state NEW -m tcp --dport 139 -j ACCEPT 
-A INPUT -s 192.168.1.0/29 -p tcp -m state --state NEW -m tcp --dport 445 -j ACCEPT 
-A INPUT -i wlan0 -p tcp -m tcp -j LOG --log-prefix "REJECT TRAFFIC " --log-level 6 
-A port-scan -p tcp -m tcp --tcp-flags FIN,SYN,RST,ACK RST -m limit --limit 1/sec -j RETURN 
-A port-scan -j DROP

```

---

### Post by teejaybee on 2010-10-15
Pidgin needs 5050/tcp outbound for yahoo to work. Maybe your established connection rule isn't working as it should?

Log all denied packets and work it out from there.

---

### Post by tad1073 on 2010-10-16
> **teejaybee said:**
> Pidgin needs 5050/tcp outbound for yahoo to work. Maybe your established connection rule isn't working as it should?

Log all denied packets and work it out from there.

will give it a try, thanks

---

