---
title: "Iptables working strangely"
date: 2017-07-25
forum: Security
---

### Post by alirezan1 on 2017-07-25
[COLOR=#242729][FONT=Arial]Hi guys


I have a system with two interfaces, wlan1 and eth0.[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]Eth0 has access to internet and wlan1 gets access to internet through eth0. I want to block access to certain websites though IP. Here is what I have done. It kills access to the IP perfectly on eth0 but not on wlan1...OR it blocks access to everything on wlan1. This is what I have and when I run it, I cannot browse internet at all[/FONT][/COLOR]
```
echo 1 > /proc/sys/net/ipv4/ip_forward
iptables -t nat -F
iptables -t nat -A POSTROUTING -o eth0 -j MASQUERADE
iptables -F        
iptables -A FORWARD -i wlan1 -o eth0 -j ACCEPT

# certain ports I need access to 
iptables -I INPUT -i wlan1 -p udp --dport 123 --sport 123 -j ACCEPT
iptables -I INPUT -i wlan1 -p udp --dport 67:68 --sport 67:68 -j ACCEPT

iptables -A OUTPUT -p udp --dport 123 -j ACCEPT
iptables -A INPUT -p udp --sport 123 -j ACCEPT
iptables -A OUTPUT -p udp -o wlan1 --dport 53 -j ACCEPT

# drop connection to 108.167.183.84 on wlan1
iptables -A OUTPUT -d 108.167.183.84 -j DROP

```

[COLOR=#242729][FONT=Arial]What I also don't understand is, if I take the last iptables command up after FORWARD, the whole thing works backwards...I get access to nothing BUT the 108.167.183.84:[/FONT][/COLOR]
```
echo 1 > /proc/sys/net/ipv4/ip_forward
iptables -t nat -F
iptables -t nat -A POSTROUTING -o eth0 -j MASQUERADE
iptables -F        
iptables -A FORWARD -i wlan1 -o eth0 -j ACCEPT

# drop connection to 108.167.183.84 on wlan1
iptables -A OUTPUT -d 108.167.183.84 -j DROP   # Without this 

# certain ports I need access to 
iptables -I INPUT -i wlan1 -p udp --dport 123 --sport 123 -j ACCEPT
iptables -I INPUT -i wlan1 -p udp --dport 67:68 --sport 67:68 -j ACCEPT

iptables -A OUTPUT -p udp --dport 123 -j ACCEPT
iptables -A INPUT -p udp --sport 123 -j ACCEPT
iptables -A OUTPUT -p udp -o wlan1 --dport 53 -j ACCEPT
```
[COLOR=#242729][FONT=Arial]
it works fine and the right way it should on the local eth0 when I'm connected to eth0. But when I try to access internet through wlan1, things don't work at all.

Can someone help me understand why this happens?[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]Thanks[/FONT][/COLOR]

---

### Post by SeijiSensei on 2017-07-26
What about this?

```
iptables -A OUTPUT **-o wlan1** -d 108.167.183.84 -j DROP
```

---

