---
title: "Block everything except for a few IP's"
date: 2018-09-17
forum: Security
---

### Post by webmiester on 2018-09-17
Hi, IF I have a computer which connects its 1st port to the ISP and the 2nd port to a router then I put the following commands:

$IPTABLES -A FORWARD -i ppp0 -o eth0 -m state --state ESTABLISHED,RELATED -j REJECT
$IPTABLES -A FORWARD -i eth0 -o ppp0 -j REJECT
$IPTABLES -t nat -A POSTROUTING -o ppp0 -j MASQUERADE

This should block all traffic to the internet right?

Now suppose I validate user with IP address of 123.123.123.45 and want to give him access to the internet, can I just type in an IPtables command that will open this connection just for him?

The other IP tables rules Ive been seeing for captive portals opens and closes port 80 but keeps the other ports open (or keeps them permanently closed).  I want something that can close everything and then when verified can open everything for a specific device.

Do you guys have any ideas on how this can be done.  I am hoping that it might be possible through an IPtables command.

---

### Post by The Cog on 2018-09-17
I am guessing that ppp0 is the ISP.

Rather than having a -j REJECT for FORWARD, it is probably better to set the default policy to reject, then allow connections that have already been allowed, then allow specific connections that you are happy with. DROP is probably better than REJECT, because REJECT can be used (by spoofing the source) to generate DDOS traffic to other hosts. Something like this (un-tested):
```

# Masquerade forwarded connections
$IPTABLES -t nat -A POSTROUTING -o ppp0 -j MASQUERADE
# Drop all forward connections by default
$IPTABLES -P FORWARD DROP
# Allow connections that have already been allowed to continue to work
$IPTABLES -A FORWARD -m state --state ESTABLISHED,RELATED -j ACCEPT
# Allow specific approved connections
IPTABLES -A FORWARD -i eth0 -o ppp0 -s 123.123.123.45 -j ACCEPT
```

---

### Post by webmiester on 2018-09-17
that sounds good.  How will the computer know what connections have already been allowed to work?

---

### Post by The Cog on 2018-09-17
The connection is remembered (in a connection tracking table) when it matches a -j ACCEPT rule (there is an inactivity timeout of a few minutes so they eventually get forgotten again). Once it is remembered it will match the ESTABLISHED,RELATED -j ACCEPT rule. So if you look at the counters agains the rules, the specific rule will only count 1 match for each new connection. The rest of the packets for a connection are counted against the ESTABLISHED rule.

---

### Post by webmiester on 2018-09-19
That is so interesting.  Thank you so much.

---

### Post by SeijiSensei on 2018-09-19
That technique is known as "stateful packet inspection."  Early commercial firewall manufacturers touted it as a design feature and charged extra for it.  Those of us using Linux have had free access to the technology since 1999-2000.

---

