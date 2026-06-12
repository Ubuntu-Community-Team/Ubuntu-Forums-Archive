---
title: "iptables OUTPUT firewall for mail server?"
date: 2019-03-25
forum: Security
---

### Post by gilgongo on 2019-03-25
I've got a mail server (running Ubuntu 16.04) which I'd like to see if I can secure by only allowing OUTBOUND connections on the various ports it uses. Inbound is working fine.

Here's the script I'm using. When I run it, I'm seeing blocked packets though like this:

```
Mar 25 16:08:11 lorina kernel: [200590.714226] IPTables-Dropped: IN= OUT=ens18 SRC=[local IP here] DST=[remote IP here] LEN=148 TOS=0x00 PREC=0x00 TTL=64 ID=37253 DF PROTO=TCP SPT=993 DPT=14826 WINDOW=243 RES=0x00 ACK PSH FIN URGP=0
```

Port 993 is one of the ports I'm allowing in the ports-to-allow.list file (the other ports are also being blocked). So is it some other rule that's blocking them?

BTW ens19 is the LAN interface, and ens18 is the WAN.

Thanks for any help.

```

iptables -A OUTPUT -o lo -p all -j ACCEPT
iptables -A OUTPUT -o ens19 -p all -j ACCEPT
iptables -A OUTPUT -p icmp -j ACCEPT
iptables -A OUTPUT -m conntrack --ctstate RELATED,ESTABLISHED -j ACCEPT
iptables -A OUTPUT -p tcp --dport 53 -j ACCEPT
iptables -A OUTPUT -p udp --dport 53 -j ACCEPT
iptables -A OUTPUT -p udp -m owner --uid-owner systemd-timesync -j ACCEPT

ip6tables -A OUTPUT -o lo -p all -j ACCEPT
ip6tables -A OUTPUT -p icmpv6 -j ACCEPT
ip6tables -A OUTPUT -m conntrack --ctstate RELATED,ESTABLISHED -j ACCEPT
ip6tables -A OUTPUT -p tcp --dport 53 -j ACCEPT
ip6tables -A OUTPUT -p udp --dport 53 -j ACCEPT
ip6tables -A OUTPUT -p udp -m owner --uid-owner systemd-timesync -j ACCEPT

while read h; do
        ip6tables -A OUTPUT -m conntrack --ctstate NEW -d $h -j ACCEPT &> /dev/null
        iptables -A OUTPUT -m conntrack --ctstate NEW -d $h -j ACCEPT
done < /usr/local/bin/hosts-to-allow.list

while read p; do
        ip6tables -A OUTPUT -m conntrack --ctstate NEW -p tcp --dport $p -j ACCEPT
        iptables -A OUTPUT -m conntrack --ctstate NEW -p tcp --dport $p -j ACCEPT
        ip6tables -A OUTPUT -m conntrack --ctstate NEW -p tcp --sport $p -j ACCEPT
        iptables -A OUTPUT -m conntrack --ctstate NEW -p tcp --sport $p -j ACCEPT
done < /usr/local/bin/ports-to-allow.list

ip6tables -A OUTPUT -o ens18 -j LOGGING
ip6tables -A LOGGING -m limit --limit 2/min -j LOG --log-prefix "IPTables-Dropped: " --log-level 4
iptables -A OUTPUT -o ens18 -j LOGGING
iptables -A LOGGING -m limit --limit 2/min -j LOG --log-prefix "IPTables-Dropped: " --log-level 4

iptables -A OUTPUT -o ens18 -j REJECT
ip6tables -A OUTPUT -o ens18 -j REJECT

```

---

### Post by Doug S on 2019-03-25
Your log line example is for a packet that is not "NEW". You can tell from the TCP flags at the end of the line.

My best guess it that this is a lingering packet from an already closed and forgotten TCP session, otherwise it would have traversed the RELATED,ESTABLISHED path.

This happens a lot with iptables, depending on your router and/or other stuff in the packets travels. Why? Because for TCP connections, Linux tends to use a "half-duplex" close sequence where either side of the session can initiate connection termination via a single 2 way FIN-ACK handshake (which puts the connection into the CLOSE_WAIT state), instead of a full 4 way FIN-ACK handshake.

Always observe the flags to know for sure what is going on. I think you are O.K.

So far in today's /var/log/syslog file I have 115 entries that end in "RES=0x00 ACK FIN URGP=0", and 93 of those are from my LAN.

---

### Post by gilgongo on 2019-03-26
Ah - thanks! That would explain why the dropped packets are happening at irregular intervals too.

Networking is more complex than it appears! :D

---

