---
title: "Torrent and security issue"
date: 2013-01-02
forum: Security
---

### Post by alfirdaous on 2013-01-02
Hello there,

I would like to allow torrent (incoming ONLY) to download from others, I used this command in my firewall iptables, but still I cannot download:

```

iptables -F iptables -X  iptables -P INPUT DROP iptables -P FORWARD DROP iptables -P OUTPUT DROP echo "Interdiction"  iptables -A INPUT -m state --state RELATED,ESTABLISHED -j ACCEPT iptables -A OUTPUT -m state --state RELATED,ESTABLISHED -j ACCEPT  iptables -A INPUT -i lo -j ACCEPT iptables -A OUTPUT -o lo -j ACCEPT  iptables -A INPUT -p tcp --dport 25 -j ACCEPT iptables -A OUTPUT -p tcp --dport 25 -j ACCEPT// Other PORTS

# Torrent
iptables -A INPUT -p tcp --destination-port 6881 -j ACCEPT
iptables -A OUTPUT -p tcp --source-port 6881 -j ACCEPT


iptables -A INPUT -p tcp --destination-port 6889 -j ACCEPT
iptables -A OUTPUT -p tcp --source-port 6889 -j ACCEPT


iptables -A INPUT -p tcp --destination-port 6969 -j ACCEPT
iptables -A OUTPUT -p tcp --source-port 6969 -j ACCEPT


iptables -A INPUT -p tcp --destination-port 7000 -j ACCEPT
iptables -A OUTPUT -p tcp --source-port 7000 -j ACCEPT


```

If any one has an indea, let me know

Thanks in advance

---

### Post by unspawn on 2013-01-03
> **alfirdaous said:**
> I would like to allow torrent (incoming ONLY) to download from others, I used this command in my firewall iptables, but still I cannot download
Your question crosses several levels. First of all, and you may not like this, on a conceptual level *how you want it to work is not how Bittorrent works*. Only leeching is, with all due respect, egotistical. *If you have concerns about bandwidth usage use a well-configurable BitTorrent client plus iptables bandwidth limiting ('man iptables': limit, recent, hashlimit also see 'man tc' and search for the LARTC "Wondershaper"). Secondly protocol-wise Bittorrent uses both UDP (majority of traffic IIRC) and TCP and a range of ports, maximally 6881-6999 IIRC, and next to that trackers may use ports like UDP/6969. Finally you chose to use your own firewall rule set over those comfortably managed by the standard tools your distribution comes with. That's OK but that means you should understand how rules work *first* (see the "Frozentux" Iptables tutorial). Notice though your default chain DROP policies makes using LOG target rules (the easiest way to debug rule set problems) impossible. I'd use ACCEPT and finish the chain with LOG and DROP targets. BTW rule order is important and you can combine rules, for example:
```

# # Keep /etc/services up to date:
# for ((i=6881;i<7000;i++)); do
# echo -en "bittorrent\t${i}/udp\t\t# Bittorrent\nbittorrent\t${i}/udp\t\t# Bittorrent\n"
# done >> /etc/services

iptables -A INPUT -i lo -j ACCEPT 
iptables -A INPUT -m state --state ESTABLISHED,RELATED -j ACCEPT
iptables -A INPUT -m state --state INVALID -j REJECT
iptables -A INPUT -p udp -m multiport --dports 6881:6999 -m state --state NEW -j ACCEPT 
iptables -A INPUT -p tcp -m multiport --dports 25,6881:6999 -m state --state NEW -j ACCEPT 
iptables -A INPUT -p icmp -j ACCEPT

```
HTH

---

