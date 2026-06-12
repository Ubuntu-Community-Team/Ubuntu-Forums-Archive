---
title: "Poor NAT performance"
date: 2008-08-20
forum: Server Platforms
---

### Post by robal on 2008-08-20
Hi,

I'm using my new 8.04 server box to share ADSL connection to my home network.

I've begun with Firestarter to setup everything.
The problem is that my interactive traffic suffers from great latency fluctuations when other user is (for e.g.) using Skype.

It came to my attention, because the same ADSL modem (when performing in router mode) does NAT way better on its own.


My configuration:

eth1 - connected to local net
eth0 - connected to ADSL modem
ppp0 - PPPoE connection via eth0

My 'iptables -L' result:
```
Chain INPUT (policy DROP)
target     prot opt source               destination
ACCEPT     tcp  --  indnsc40.ukcore.bt.net  anywhere            tcp flags:!FIN,SYN,RST,ACK/SYN
ACCEPT     udp  --  ns6.bt.net           anywhere
ACCEPT     tcp  --  indnsc61.ukcore.bt.net  anywhere            tcp flags:!FIN,SYN,RST,ACK/SYN
ACCEPT     udp  --  indnsc61.ukcore.bt.net  anywhere
ACCEPT     all  --  anywhere             anywhere
ACCEPT     icmp --  anywhere             anywhere            limit: avg 10/sec burst 5
DROP       all  --  BASE-ADDRESS.MCAST.NET/8  anywhere
DROP       all  --  anywhere             BASE-ADDRESS.MCAST.NET/8
DROP       all  --  255.255.255.255      anywhere
DROP       all  --  anywhere             0.0.0.0
DROP       all  --  anywhere             anywhere            state INVALID
LSI        all  -f  anywhere             anywhere            limit: avg 10/min burst 5
INBOUND    all  --  anywhere             anywhere
INBOUND    all  --  anywhere             192.168.0.1
INBOUND    all  --  anywhere             host86-138-146-109.range86-138.btcentralplus.com
INBOUND    all  --  anywhere             192.168.0.255
LOG_FILTER  all  --  anywhere             anywhere
LOG        all  --  anywhere             anywhere            LOG level info prefix `Unknown Input'

Chain FORWARD (policy DROP)
target     prot opt source               destination
ACCEPT     icmp --  anywhere             anywhere            limit: avg 10/sec burst 5
TCPMSS     tcp  --  anywhere             anywhere            tcp flags:SYN,RST/SYN TCPMSS clamp to PMTU
OUTBOUND   all  --  anywhere             anywhere
ACCEPT     tcp  --  anywhere             link-local/24       state RELATED,ESTABLISHED
ACCEPT     udp  --  anywhere             link-local/24       state RELATED,ESTABLISHED
LOG_FILTER  all  --  anywhere             anywhere
LOG        all  --  anywhere             anywhere            LOG level info prefix `Unknown Forward'

Chain OUTPUT (policy DROP)
target     prot opt source               destination
ACCEPT     tcp  --  host86-138-146-109.range86-138.btcentralplus.com  indnsc40.ukcore.bt.net tcp dpt:domain
ACCEPT     udp  --  host86-138-146-109.range86-138.btcentralplus.com  ns6.bt.net          udp dpt:domain
ACCEPT     tcp  --  host86-138-146-109.range86-138.btcentralplus.com  indnsc61.ukcore.bt.net tcp dpt:domain
ACCEPT     udp  --  host86-138-146-109.range86-138.btcentralplus.com  indnsc61.ukcore.bt.net udp dpt:domain
ACCEPT     all  --  anywhere             anywhere
DROP       all  --  BASE-ADDRESS.MCAST.NET/8  anywhere
DROP       all  --  anywhere             BASE-ADDRESS.MCAST.NET/8
DROP       all  --  255.255.255.255      anywhere
DROP       all  --  anywhere             0.0.0.0
DROP       all  --  anywhere             anywhere            state INVALID
OUTBOUND   all  --  anywhere             anywhere
OUTBOUND   all  --  anywhere             anywhere
LOG_FILTER  all  --  anywhere             anywhere
LOG        all  --  anywhere             anywhere            LOG level info prefix `Unknown Output'

Chain INBOUND (4 references)
target     prot opt source               destination
ACCEPT     tcp  --  anywhere             anywhere            state RELATED,ESTABLISHED
ACCEPT     udp  --  anywhere             anywhere            state RELATED,ESTABLISHED
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:ssh
ACCEPT     udp  --  anywhere             anywhere            udp dpt:ssh
ACCEPT     tcp  --  link-local/24        anywhere            tcp dpt:www
ACCEPT     udp  --  link-local/24        anywhere            udp dpt:www
ACCEPT     tcp  --  link-local/24        anywhere            tcp dpt:microsoft-ds
ACCEPT     udp  --  link-local/24        anywhere            udp dpt:microsoft-ds
ACCEPT     tcp  --  link-local/24        anywhere            tcp dpt:netbios-ssn
ACCEPT     udp  --  link-local/24        anywhere            udp dpt:netbios-ssn
ACCEPT     tcp  --  link-local/24        anywhere            tcp dpt:netbios-dgm
ACCEPT     udp  --  link-local/24        anywhere            udp dpt:netbios-dgm
ACCEPT     tcp  --  link-local/24        anywhere            tcp dpt:netbios-ns
ACCEPT     udp  --  link-local/24        anywhere            udp dpt:netbios-ns
ACCEPT     tcp  --  link-local/24        anywhere            tcp dpt:mysql
ACCEPT     udp  --  link-local/24        anywhere            udp dpt:mysql
ACCEPT     tcp  --  link-local/24        anywhere            tcp dpt:xdmcp
ACCEPT     udp  --  link-local/24        anywhere            udp dpt:xdmcp
ACCEPT     tcp  --  link-local/24        anywhere            tcp dpts:bootps:bootpc
ACCEPT     udp  --  link-local/24        anywhere            udp dpts:bootps:bootpc
ACCEPT     tcp  --  link-local/24        anywhere            tcp dpt:domain
ACCEPT     udp  --  link-local/24        anywhere            udp dpt:domain
LSI        all  --  anywhere             anywhere

Chain LOG_FILTER (5 references)
target     prot opt source               destination

Chain LSI (2 references)
target     prot opt source               destination
LOG_FILTER  all  --  anywhere             anywhere
LOG        tcp  --  anywhere             anywhere            tcp flags:FIN,SYN,RST,ACK/SYN limit: avg 1/sec burst 5 LOG level info prefix `Inbound '
DROP       tcp  --  anywhere             anywhere            tcp flags:FIN,SYN,RST,ACK/SYN
LOG        tcp  --  anywhere             anywhere            tcp flags:FIN,SYN,RST,ACK/RST limit: avg 1/sec burst 5 LOG level info prefix `Inbound '
DROP       tcp  --  anywhere             anywhere            tcp flags:FIN,SYN,RST,ACK/RST
LOG        icmp --  anywhere             anywhere            icmp echo-request limit: avg 1/sec burst 5 LOG level info prefix `Inbound '
DROP       icmp --  anywhere             anywhere            icmp echo-request
LOG        all  --  anywhere             anywhere            limit: avg 5/sec burst 5 LOG level info prefix `Inbound '
DROP       all  --  anywhere             anywhere

Chain LSO (0 references)
target     prot opt source               destination
LOG_FILTER  all  --  anywhere             anywhere
LOG        all  --  anywhere             anywhere            limit: avg 5/sec burst 5 LOG level info prefix `Outbound '
REJECT     all  --  anywhere             anywhere            reject-with icmp-port-unreachable

Chain OUTBOUND (3 references)
target     prot opt source               destination
ACCEPT     icmp --  anywhere             anywhere
ACCEPT     tcp  --  anywhere             anywhere            state RELATED,ESTABLISHED
ACCEPT     udp  --  anywhere             anywhere            state RELATED,ESTABLISHED
ACCEPT     all  --  anywhere             anywhere
```


BTW:  Is it normal that 'iptables -L' takes 2 minutes to print chains ? Other than that, this PC is quite responsive and fast.
Isn't this iptables configuration too hairy ?  Maybe Firestarter is to blame ?



Any hints would be much apreciated.

---

### Post by Ximbiot on 2008-08-20
> **robal said:**
> I've begun with Firestarter to setup everything.
The problem is that my interactive traffic suffers from great latency fluctuations when other user is (for e.g.) using Skype.

This sounds like a simple bandwidth availability issue and likely has nothing to do with NAT (other than that you are using NAT to share the same connection and thus that connection's total bandwidth).  You might look into the the --set-tos option available in iptable's mangle table.  It lets you put some basic type-of-service settings on different ports, like "low-latency" for ssh/22, "high-bandwidth" for voip, and "minimize-cost" for smtp/25.

You can get more specific with the tc (traffic control) command, though it is corresponding harder to use.  tc lets you set up different routing queues with bandwidth minimums/maximums and different queue handling algorithms based on anything you can select and mark with iptables commands.

For more, see the [Linux Advanced Routing & Traffic Control HOWTO]("http://lartc.org/howto/") or google using terms like "iptables", "low-latency", "high-bandwidth", "limit bandwidth", etc.

> **robal said:**
> BTW: Is it normal that 'iptables -L' takes 2 minutes to print chains ? Other than that, this PC is quite responsive and fast.

It's normal for me over quite a few sets of hardware and linux distributions.  I'm not sure what the explanation is.

---

