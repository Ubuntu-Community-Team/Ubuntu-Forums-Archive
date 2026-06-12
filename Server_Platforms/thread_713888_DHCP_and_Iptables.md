---
title: "DHCP and Iptables"
date: 2008-03-03
forum: Server Platforms
---

### Post by Stephen_at on 2008-03-03
Got an annoying problem.

Here is the setup:

ADSL Router----Linux Server
  |
  |
  Windows PC(s)

The Linux server is running some local services (print, filesharing etc) and also runs as the DHCP server and does DNS too (because the DHCP/DNS server on the ADSL router is lousy).

All works fine. Until I turn the firewall on on the Linux box.

With a Gui tool like Firestarter I can see the DNS requests and allow them through but DHCP isn't seen and if I add a rule to the Policy in Firestarter it make no difference.

If I stop the firewall then DHCP works fine.

---

### Post by faulkes on 2008-03-03
after inserting the DHCP rule into Firestarter, open a terminal and issue:

```

sudo iptables -L -n

```

Copy the results back here so people can see if the rules are correct.

Faulkes

---

### Post by Stephen_at on 2008-03-03
OK firestarter Inbound Policy shows I'm allowing inbound for :

DNS (53), DHCP (67-68), HTTP (80) Samba (137, 139), Microsoft-ds(445) and SSH (22)


the iptables command shows:

[FONT="Courier New"]Chain INBOUND (1 references)
target     prot opt source               destination
ACCEPT     tcp  --  0.0.0.0/0            0.0.0.0/0           state RELATED,ESTABLISHED
ACCEPT     udp  --  0.0.0.0/0            0.0.0.0/0           state RELATED,ESTABLISHED
ACCEPT     tcp  --  0.0.0.0/0            0.0.0.0/0           tcp dpt:53
ACCEPT     udp  --  0.0.0.0/0            0.0.0.0/0           udp dpt:53
ACCEPT     tcp  --  0.0.0.0/0            0.0.0.0/0           tcp dpts:67:68
ACCEPT     udp  --  0.0.0.0/0            0.0.0.0/0           udp dpts:67:68
ACCEPT     tcp  --  0.0.0.0/0            0.0.0.0/0           tcp dpt:80
ACCEPT     udp  --  0.0.0.0/0            0.0.0.0/0           udp dpt:80
ACCEPT     tcp  --  0.0.0.0/0            0.0.0.0/0           tcp dpt:137
ACCEPT     udp  --  0.0.0.0/0            0.0.0.0/0           udp dpt:137
ACCEPT     tcp  --  0.0.0.0/0            0.0.0.0/0           tcp dpt:22
ACCEPT     udp  --  0.0.0.0/0            0.0.0.0/0           udp dpt:22
ACCEPT     tcp  --  0.0.0.0/0            0.0.0.0/0           tcp dpt:445
ACCEPT     udp  --  0.0.0.0/0            0.0.0.0/0           udp dpt:445
ACCEPT     tcp  --  0.0.0.0/0            0.0.0.0/0           tcp dpt:139
ACCEPT     udp  --  0.0.0.0/0            0.0.0.0/0           udp dpt:139
LSI        all  --  0.0.0.0/0            0.0.0.0/0

Chain INPUT (policy DROP)
target     prot opt source               destination
ACCEPT     tcp  --  127.0.0.1            0.0.0.0/0           tcp flags:!0x17/0x02
ACCEPT     udp  --  127.0.0.1            0.0.0.0/0
ACCEPT     tcp  --  212.159.6.10         0.0.0.0/0           tcp flags:!0x17/0x02
ACCEPT     udp  --  212.159.6.10         0.0.0.0/0
ACCEPT     tcp  --  212.159.6.9          0.0.0.0/0           tcp flags:!0x17/0x02
ACCEPT     udp  --  212.159.6.9          0.0.0.0/0
ACCEPT     tcp  --  208.67.222.222       0.0.0.0/0           tcp flags:!0x17/0x02
ACCEPT     udp  --  208.67.222.222       0.0.0.0/0
ACCEPT     tcp  --  208.67.220.220       0.0.0.0/0           tcp flags:!0x17/0x02
ACCEPT     udp  --  208.67.220.220       0.0.0.0/0
ACCEPT     all  --  0.0.0.0/0            0.0.0.0/0
ACCEPT     icmp --  0.0.0.0/0            0.0.0.0/0           limit: avg 10/sec burst 5
DROP       all  --  0.0.0.0/0            255.255.255.255
DROP       all  --  0.0.0.0/0            192.168.255.255
DROP       all  --  224.0.0.0/8          0.0.0.0/0
DROP       all  --  0.0.0.0/0            224.0.0.0/8
DROP       all  --  255.255.255.255      0.0.0.0/0
DROP       all  --  0.0.0.0/0            0.0.0.0
DROP       all  --  0.0.0.0/0            0.0.0.0/0           state INVALID
LSI        all  -f  0.0.0.0/0            0.0.0.0/0           limit: avg 10/min burst 5
INBOUND    all  --  0.0.0.0/0            0.0.0.0/0
ACCEPT     udp  --  0.0.0.0/0            0.0.0.0/0           udp spts:67:68 dpts:67:68
LOG_FILTER  all  --  0.0.0.0/0            0.0.0.0/0
LOG        all  --  0.0.0.0/0            0.0.0.0/0           LOG flags 0 level 6 prefix `Unknown Input'

Chain FORWARD (policy DROP)
target     prot opt source               destination
ACCEPT     icmp --  0.0.0.0/0            0.0.0.0/0           limit: avg 10/sec burst 5
LOG_FILTER  all  --  0.0.0.0/0            0.0.0.0/0
LOG        all  --  0.0.0.0/0            0.0.0.0/0           LOG flags 0 level 6 prefix `Unknown Forward'

Chain LOG_FILTER (5 references)
target     prot opt source               destination

Chain LSI (2 references)
target     prot opt source               destination
LOG_FILTER  all  --  0.0.0.0/0            0.0.0.0/0
LOG        tcp  --  0.0.0.0/0            0.0.0.0/0           tcp flags:0x17/0x02 limit: avg 1/sec burst 5 LOG flags 0 level 6 prefix `Inbound '
DROP       tcp  --  0.0.0.0/0            0.0.0.0/0           tcp flags:0x17/0x02
LOG        tcp  --  0.0.0.0/0            0.0.0.0/0           tcp flags:0x17/0x04 limit: avg 1/sec burst 5 LOG flags 0 level 6 prefix `Inbound '
DROP       tcp  --  0.0.0.0/0            0.0.0.0/0           tcp flags:0x17/0x04
LOG        icmp --  0.0.0.0/0            0.0.0.0/0           icmp type 8 limit: avg 1/sec burst 5 LOG flags 0 level 6 prefix `Inbound '
DROP       icmp --  0.0.0.0/0            0.0.0.0/0           icmp type 8
LOG        all  --  0.0.0.0/0            0.0.0.0/0           limit: avg 5/sec burst 5 LOG flags 0 level 6 prefix `Inbound '
DROP       all  --  0.0.0.0/0            0.0.0.0/0

Chain LSO (0 references)
target     prot opt source               destination
LOG_FILTER  all  --  0.0.0.0/0            0.0.0.0/0
LOG        all  --  0.0.0.0/0            0.0.0.0/0           limit: avg 5/sec burst 5 LOG flags 0 level 6 prefix `Outbound '
REJECT     all  --  0.0.0.0/0            0.0.0.0/0           reject-with icmp-port-unreachable

Chain OUTBOUND (1 references)
target     prot opt source               destination
ACCEPT     icmp --  0.0.0.0/0            0.0.0.0/0
ACCEPT     tcp  --  0.0.0.0/0            0.0.0.0/0           state RELATED,ESTABLISHED
ACCEPT     udp  --  0.0.0.0/0            0.0.0.0/0           state RELATED,ESTABLISHED
ACCEPT     all  --  0.0.0.0/0            0.0.0.0/0

Chain OUTPUT (policy DROP)
target     prot opt source               destination
ACCEPT     tcp  --  192.168.0.2          127.0.0.1           tcp dpt:53
ACCEPT     udp  --  192.168.0.2          127.0.0.1           udp dpt:53
ACCEPT     tcp  --  192.168.0.2          212.159.6.10        tcp dpt:53
ACCEPT     udp  --  192.168.0.2          212.159.6.10        udp dpt:53
ACCEPT     tcp  --  192.168.0.2          212.159.6.9         tcp dpt:53
ACCEPT     udp  --  192.168.0.2          212.159.6.9         udp dpt:53
ACCEPT     tcp  --  192.168.0.2          208.67.222.222      tcp dpt:53
ACCEPT     udp  --  192.168.0.2          208.67.222.222      udp dpt:53
ACCEPT     tcp  --  192.168.0.2          208.67.220.220      tcp dpt:53
ACCEPT     udp  --  192.168.0.2          208.67.220.220      udp dpt:53
ACCEPT     all  --  0.0.0.0/0            0.0.0.0/0
DROP       all  --  224.0.0.0/8          0.0.0.0/0
DROP       all  --  0.0.0.0/0            224.0.0.0/8
DROP       all  --  255.255.255.255      0.0.0.0/0
DROP       all  --  0.0.0.0/0            0.0.0.0
DROP       all  --  0.0.0.0/0            0.0.0.0/0           state INVALID
OUTBOUND   all  --  0.0.0.0/0            0.0.0.0/0
LOG_FILTER  all  --  0.0.0.0/0            0.0.0.0/0
LOG        all  --  0.0.0.0/0            0.0.0.0/0           LOG flags 0 level 6 prefix `Unknown Output'
[/FONT]

Which shows that its got 67 and 68 in there and on UDP so....

I'm using dnsmasq to provide DNS and DHCP...

I even manually installed dnsmasq  so I'm running on the following versions:

dnsmasq : version 2.41 
iptables v1.3.3

---

### Post by faulkes on 2008-03-03
> **Stephen_at said:**
> 
the iptables command shows:

[FONT=Courier New]Chain INBOUND (1 references)
ACCEPT     tcp  --  0.0.0.0/0            0.0.0.0/0           tcp dpts:67:68
ACCEPT     udp  --  0.0.0.0/0            0.0.0.0/0           udp dpts:67:68


This appears fine here, iirc though, INPUT is parsed first,
then additional chains, so INBOUND is parsed at the end
of INPUT. 

> 
Chain INPUT (policy DROP)
target     prot opt source               destination
[B]DROP       all  --  0.0.0.0/0            255.255.255.255
DROP       all  --  0.0.0.0/0            192.168.255.255
DROP       all  --  255.255.255.255      0.0.0.0/0[/B]
DROP       all  --  0.0.0.0/0            0.0.0.0
DROP       all  --  0.0.0.0/0            0.0.0.0/0           state INVALID
LSI        all  -f  0.0.0.0/0            0.0.0.0/0           limit: avg 10/min burst 5
INBOUND    all  --  0.0.0.0/0            0.0.0.0/0
** ACCEPT     udp  --  0.0.0.0/0            0.0.0.0/0           udp spts:67:68 dpts:67:68**
LOG_FILTER  all  --  0.0.0.0/0            0.0.0.0/0
LOG        all  --  0.0.0.0/0            0.0.0.0/0           LOG flags 0 level 6 prefix `Unknown Input'


So I would question the above rules, with a policy of DROP
in the input chain, I would guess it is matching those for
DHCP (Others feel free to correct me on this).

[/FONT]> 
Which shows that its got 67 and 68 in there and on UDP so....

I'm using dnsmasq to provide DNS and DHCP...

I even manually installed dnsmasq  so I'm running on the following versions:

dnsmasq : version 2.41 
iptables v1.3.3

Is there a requirement for you to use your own internal DNS or can't you just
point at/use your providers (standard DHCP would allow you to assign that)?

Faulkes

---

### Post by Stephen_at on 2008-03-03
DNS isn't a problem - its working fine and its very quick. I'm using it for various reasons. Its just the DHCP which is being killed stone dead.

Maybe I need to use a different tool to play with the iptables rules.

---

### Post by faulkes on 2008-03-03
> **Stephen_at said:**
> DNS isn't a problem - its working fine and its very quick. I'm using it for various reasons. Its just the DHCP which is being killed stone dead.

Maybe I need to use a different tool to play with the iptables rules.

dnsmask provides for dhcp and dns, one of which you have a problem
with.  it adds rules to iptables, rules which really aren't needed (IMO) for
what you are trying to achieve and are causing problems as you are also
using Firestarter.

My suggestion is to use the standard dhcp server which ships with
ubuntu server and configure iptables using only firestarter or alternatively
the ufw package (ubuntu firewall).

Faulkes

---

### Post by Stephen_at on 2008-03-04
I just purged the iptable rules and am running without it at the moment as I'm behind a router which is blocking most ports (its only got pop3s, smtp, SSH, HTTP and HTTPS open).

If I can ever get my head round the rather complex logic I might try creating my own rule set and manually setting it all up - even if its only to block most of Korean and Taiwan from trying to use my locked down email server as a relay.

My old server has got APF running on it and thats easy to configure and it just links to iptables...

So what I'm thinking of is:

1) Trust my local network (unless someone is going to sneak into my house and plug a cable into my router I know exactly what machines I have on my network and can restrict DHCP to specific MACs)
2) As the router is only forwarding some traffic I dont need a lot of server based rules.
3) Server based rules to limit access to some services to specific address ranges. I'm already using hosts.deny to lock down SSH connections. POP3S is only used by me when I'm out on the road and I dont see any attempts to misuse it. SMTP is the big one - my ISP (Plusnet) pushes incoming emails to me so I've got to allow them in and they have a large number of servers which can push to me. Also I send email through my server when I'm not at home (using POPbeforeSMTP for security) so I need to have it open for that. But the rest of the world is not important  so they can be blocked.

---

