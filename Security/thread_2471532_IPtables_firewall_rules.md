---
title: "IPtables firewall rules"
date: 2022-02-02
forum: Security
---

### Post by xgeek652 on 2022-02-02
[COLOR=#232629][FONT=-apple-system]Can you please explain to me the difference between this 2 IPtables rules, there were implemented to transfer packets from external internet users to a local server :

[/FONT][/COLOR][HTML]iptables -t nat -A PREROUTING -p tcp -d $IFACE_INTERNET --dport 443 -j DNAT --to-destination $WEB_SERVER

iptables -A FORWARD -p TCP -i $IFACE_INTERNET -d $WEB_SERVER --dport 443 -j ACCEPT[/HTML]

[COLOR=#232629][FONT=-apple-system]If only "NAT" rule is implemented we won't be able to access the server.[/FONT][/COLOR]
[COLOR=#232629][FONT=-apple-system]Thanks[/FONT][/COLOR]

---

### Post by SeijiSensei on 2022-02-02
The first rule just rewrites the packet to have a local source address. The second enables the packet to be forwarded to the server.

My guess is that somewhere in the iptables rules there is a 
```
iptables -P FORWARD DROP
```
that sets the default policy for the FORWARD chain to dropping packets rather than forwarding them. Without the second rule to override that default, packets will not go to the web server.

---

