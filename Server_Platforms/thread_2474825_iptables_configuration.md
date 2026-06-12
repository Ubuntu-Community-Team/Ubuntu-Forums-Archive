---
title: "iptables configuration"
date: 2022-05-09
forum: Server Platforms
---

### Post by rsteinmetz70112 on 2022-05-09
I have been getting notices form my ISP that there is an open port on one of my static IP addresses. The Static Address is assigned to a Windows Server. The network uses iptables running on a Ubuntu 18.04 computer to do NAT and configure the external firewall. What happens is Static Public IP Address => Private IP address I've tried to block the port in IPtables using statements like this:

```
-A INPUT -d w.x.y.z/32 -p udp -m udp --dport <port> -j DROP
-A OUTPUT -d w.x.y.x/32 -p udp -m udp --dport <port> -j DROP
-A INPUT -d w.x.y.z/29 -p udp -m udp --dport <port> -j DROP
-A OUTPUT -d w.x.y.z/29 -p udp -m udp --dport <port> -j DROP
```

The /32 should operate only on a single IP address but the /29 should block the whole range.

I also have similar statements for tcp I omitted them to simplify.

What am I doing wrong?

---

### Post by #&amp;thj^% on 2022-05-09
You can use **"sudo iptables -L -nv**" to troubleshoot if the rules are matched. You will see in the first column** pkts** the number of packets that matched each rule.
I follow this mostly: [https://www.freecodecamp.org/news/subnet-cheat-sheet-24-subnet-mask-30-26-27-29-and-other-ip-address-cidr-network-references/](https://www.freecodecamp.org/news/subnet-cheat-sheet-24-subnet-mask-30-26-27-29-and-other-ip-address-cidr-network-references/)
Sometimes its easier to see associated values with line numbers.
```
sudo iptables -nvL --line-numbers

```

---

### Post by rsteinmetz70112 on 2022-05-09
Unfortunately my ISP is only testing for open ports. When I check the actual traffic I don't see much. A small number of udp packets to w.x.y.z/29 are being dropped, but is doesn't report the specific ip address. Mostly what I see are fail2ban rejects.

---

### Post by #&amp;thj^% on 2022-05-09
You may need more *valid support from your ISP.

---

### Post by Doug S on 2022-05-09
I think we need more information. We might need to see your rules within the context of your overall iptables rule set. You might need to add DROP rules to your FORWARD chain, not sure.

I agree with 1fallen about using the packet counters as a debugging aid. Also adding specific logging rules can help, but be careful not make big huge log files as a result. I also like to use tcpdump (or wireshark, if your prefer) to correlate the iptables rule set with the actual coming and going of packets.

---

### Post by The Cog on 2022-05-09
Apart from being short on usable information, one thing that comes to mind is that if you are using the Ubuntu as a firewall then you need to be looking at the FORWARD chain, not the INPUT and OUTPUT chains which only affect traffic to/from the Ubuntu OS itself.

---

### Post by #&amp;thj^% on 2022-05-09
> **The Cog said:**
> Apart from being short on usable information, one thing that comes to mind is that if you are using the Ubuntu as a firewall then you need to be looking at the FORWARD chain, not the INPUT and OUTPUT chains which only affect traffic to/from the Ubuntu OS itself.

+1 I guess I shouldn't have just hinted at it.
Thanks The Cog

---

### Post by rsteinmetz70112 on 2022-05-09
Looking at my iptables rule set I don't actually have any FORWARD rules. As far as Firewall, the primary firewall is my router, the iptables computer functions as a NAT router for the static IP addresses to distribute them to the specific computers. Each computer also runs a firewall and as far as I can see the Ubuntu computers work fine, it's the one Windows Server that seem to have an open port being detected. I guess I could wait a while and see if the latest batch of adjustments solve the problem.

Running nmap on the tcp port gives me the port is "filtered", but running nmap on the udp  port I get "open|filtered"

---

### Post by Doug S on 2022-05-09
No iptables rules in the FORWARD chain does not mean it isn't been used, particularly if the default policy is ACCEPT. You can check via the command 1fallen gave. Example (I use a slightly different command):

```
doug@s15:~$ [COLOR="#FF0000"]sudo iptables -xvnL[/COLOR]
...
Chain FORWARD (policy DROP [COLOR="#FF0000"]5 packets[/COLOR], 201 bytes)
    pkts      bytes target     prot opt in     out     source               destination
       3      234 DROP       udp  --  *      enp1s0  0.0.0.0/0            0.0.0.0/0            udp dpt:137
     290    22438 LOG        all  --  *      enp1s0  0.0.0.0/0            192.168.0.0/16       LOG flags 0 level 6 prefix "F192:"
     290    22438 DROP       all  --  *      enp1s0  0.0.0.0/0            192.168.0.0/16
      58     5792 LOG        all  --  *      enp1s0  0.0.0.0/0            10.0.0.0/8           LOG flags 0 level 6 prefix "F10:"
      58     5792 DROP       all  --  *      enp1s0  0.0.0.0/0            10.0.0.0/8
       0        0 LOG        all  --  *      enp1s0  0.0.0.0/0            172.16.0.0/12        LOG flags 0 level 6 prefix "F172:"
       0        0 DROP       all  --  *      enp1s0  0.0.0.0/0            172.16.0.0/12
       0        0 LOG        all  --  *      enp1s0  0.0.0.0/0            224.0.0.0/4          LOG flags 0 level 6 prefix "F224:"
       0        0 DROP       all  --  *      enp1s0  0.0.0.0/0            224.0.0.0/4
       0        0 LOG        all  --  *      enp1s0  0.0.0.0/0            240.0.0.0/5          LOG flags 0 level 6 prefix "F240:"
       0        0 DROP       all  --  *      enp1s0  0.0.0.0/0            240.0.0.0/5
       1      146 LOG        all  --  *      enp1s0  0.0.0.0/0            169.254.0.0/16       LOG flags 0 level 6 prefix "F169:"
       1      146 DROP       all  --  *      enp1s0  0.0.0.0/0            169.254.0.0/16
   57830  2793564 REJECT     all  --  br0    *       0.0.0.0/0            0.0.0.0/0            state INVALID reject-with icmp-port-unreachable
       0        0 DROP       all  --  br0    enp1s0  192.168.111.101      0.0.0.0/0
218409041 353604961902 ACCEPT     all  --  enp1s0 br0     0.0.0.0/0            0.0.0.0/0            state RELATED,ESTABLISHED
129437007 37175308582 ACCEPT     all  --  br0    enp1s0  0.0.0.0/0            0.0.0.0/0
       0        0 LOG        all  --  *      *       0.0.0.0/0            0.0.0.0/0            LOG flags 0 level 6 prefix "FCATCH:"
       0        0 DROP       all  --  *      *       0.0.0.0/0            0.0.0.0/0
...
```Note that the 5 packets are due to re-loading my rules script on the fly, as once all the rules are in place there is no way to ever get there.

---

### Post by rsteinmetz70112 on 2022-05-09
OK I ran your command and this is what I got for FORWARD:
```
Chain FORWARD (policy ACCEPT 42 packets, 1758 bytes)
    pkts      bytes target     prot opt in     out     source               destination
```

Looking at INPUT and OUTPUT I don't see any packets going to the ports I'm trying to block. 

I also have pairs of PREROUTING and  POSTROUTING rules to do address translation each of my Static IP addresses.

```
-A PREROUTING -d xx.xx.xx.xx/32 -j DNAT --to-destination 192.168.1.29
-A POSTROUTING -s 192.168.1.29/32 -j SNAT --to-source xx.xx.xx.xx
-A POSTROUTING -o enp1s0 -j MASQUERADE

```

---

### Post by Doug S on 2022-05-09
O.K. so 42 packets have traversed your FORWARD chain.
My suggestion is to add a temporary logging rule to your FORWARD chain so that you know what the traffic is:

```
sudo iptables -A FORWARD -j LOG --log-prefix "FCATCH:" --log-level info
```
Again, be careful is case there is a lot of traffic that might bloat your logs. OR add a port specific logging rule.

---

### Post by rsteinmetz70112 on 2022-05-10
OK I added the rule you suggested. so far no traffic on the port I'm trying to block.

---

### Post by rsteinmetz70112 on 2022-06-15
I've starting getting repots from my ISP again. I guess I'll have to try some new things with iptables to finally block the port.

---

### Post by Doug S on 2022-06-15
A few of us have chimed in on this thread, and I suspect several more might be willing to help. The issues remains that we have very little information and therefore struggle to be of any help.

---

### Post by rsteinmetz70112 on 2022-06-17
What information do you need. I'm reluctant to provide too much specific details as I don't want to become a target. I already get plenty of probes looking to break in.

---

### Post by Doug S on 2022-06-18
> **rsteinmetz70112 said:**
> What information do you need. I'm reluctant to provide too much specific details as I don't want to become a target. I already get plenty of probes looking to break in.Without your IP address, I do not know what the concern is. You will always get plenty of probes regardless.

For my part, I still do not understand your network. It seems as though there is a modem between your server and the internet, but you said "As far as Firewall, the primary firewall is my router", which begs the question why not block the port there? If packets are flowing through your NAT server to the destination servers, then I would have expected the FORWARD chain packet count to be much much higher than the 42 you listed on May 9th, unless the packet counters had just been reset.

Anyway, if it were me, and if all packets indeed flow through your NAT server, then I would continue to monitor with the iptables rule I listed on May 9th and also set up a tcpdump (or wireshark if you prefer) to monitor traffic to/from the problematic port. By the way, why does your ISP care if a port is open? please give more details about the issue.

Why do you mix SNAT and MASQUERADE? And which interface is "enp1s0"? I do not understand this line: -A POSTROUTING -o enp1s0 -j MASQUERADE.

If packets actually do flow via the FORWARD chain then I suspect you need something like:

```

-A FORWARD -i $EXTIF -d 192.168.1.29 -p udp -m udp --dport <port> -j DROP

```Where $EXTIF is the WAN facing network interface card and 192.168.1.29 is the LAN address of the windows server. Similarly for TCP. I did not test the syntax.

EDIT: I made a mistake, the IP address would be as per the DNAT from the PREROUTING at this point. Fix it.

---

