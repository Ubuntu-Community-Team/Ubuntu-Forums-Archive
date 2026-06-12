---
title: "Ubuntu 23.10, iptables not banning IPs..."
date: 2023-10-26
forum: Security
---

### Post by sblantipodi on 2023-10-26
Hi all,
using Ubuntu 23.10 server.

My IP tables is not banning IPs and I don't understand why...

I tried to start from scratch with a reset... this are the command from scratch.

ufw disable;

ufw reset;

ufw allow 22;
ufw allow 8124; (my web server port)

ufw default deny;

ufw enable;

iptables -A INPUT -s 176.xxx.xxx.xxx -j DROP;

iptables -L;

```
iptables -LChain INPUT (policy DROP)
target     prot opt source               destination         
f2b-HASS   tcp  --  anywhere             anywhere            
ufw-before-logging-input  all  --  anywhere             anywhere            
ufw-before-input  all  --  anywhere             anywhere            
ufw-after-input  all  --  anywhere             anywhere            
ufw-after-logging-input  all  --  anywhere             anywhere            
ufw-reject-input  all  --  anywhere             anywhere            
ufw-track-input  all  --  anywhere             anywhere            
ACCEPT     tcp  --  anywhere             anywhere             tcp dpt:http
ACCEPT     tcp  --  anywhere             anywhere             tcp dpt:81
ACCEPT     tcp  --  anywhere             anywhere             tcp dpt:https
ACCEPT     tcp  --  anywhere             anywhere             tcp dpt:8124
ACCEPT     tcp  --  anywhere             anywhere             tcp dpt:8123
[B]DROP       all  --  176.xxx.xxx.xxx       anywhere            
[/B]

Chain FORWARD (policy DROP)
target     prot opt source               destination         
DOCKER-USER  all  --  anywhere             anywhere            
DOCKER-ISOLATION-STAGE-1  all  --  anywhere             anywhere            
ACCEPT     all  --  anywhere             anywhere             ctstate RELATED,ESTABLISHED
DOCKER     all  --  anywhere             anywhere            
ACCEPT     all  --  anywhere             anywhere            
ACCEPT     all  --  anywhere             anywhere            
ACCEPT     all  --  anywhere             anywhere             ctstate RELATED,ESTABLISHED
DOCKER     all  --  anywhere             anywhere            
ACCEPT     all  --  anywhere             anywhere            
ACCEPT     all  --  anywhere             anywhere            
ufw-before-logging-forward  all  --  anywhere             anywhere            
ufw-before-forward  all  --  anywhere             anywhere            
ufw-after-forward  all  --  anywhere             anywhere            
ufw-after-logging-forward  all  --  anywhere             anywhere            
ufw-reject-forward  all  --  anywhere             anywhere            
ufw-track-forward  all  --  anywhere             anywhere            


Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination         
ufw-before-logging-output  all  --  anywhere             anywhere            
ufw-before-output  all  --  anywhere             anywhere            
ufw-after-output  all  --  anywhere             anywhere            
ufw-after-logging-output  all  --  anywhere             anywhere            
ufw-reject-output  all  --  anywhere             anywhere            
ufw-track-output  all  --  anywhere             anywhere            


Chain DOCKER (2 references)
target     prot opt source               destination         
ACCEPT     tcp  --  anywhere             172.26.0.2           tcp dpt:9000
ACCEPT     tcp  --  anywhere             172.26.0.3           tcp dpt:nut
ACCEPT     tcp  --  anywhere             172.26.0.4           tcp dpt:1883
ACCEPT     tcp  --  anywhere             172.26.0.6           tcp dpt:8124
ACCEPT     tcp  --  anywhere             172.26.0.6           tcp dpt:81


Chain DOCKER-ISOLATION-STAGE-1 (1 references)
target     prot opt source               destination         
DOCKER-ISOLATION-STAGE-2  all  --  anywhere             anywhere            
DOCKER-ISOLATION-STAGE-2  all  --  anywhere             anywhere            
RETURN     all  --  anywhere             anywhere            


Chain DOCKER-ISOLATION-STAGE-2 (2 references)
target     prot opt source               destination         
DROP       all  --  anywhere             anywhere            
DROP       all  --  anywhere             anywhere            
RETURN     all  --  anywhere             anywhere            


Chain DOCKER-USER (1 references)
target     prot opt source               destination         
RETURN     all  --  anywhere             anywhere            


Chain f2b-HASS (1 references)
target     prot opt source               destination         
**REJECT     all  --  176.xxx.xxx.xxx       anywhere             reject-with icmp-port-unreachable**
RETURN     all  --  anywhere             anywhere          

Chain ufw-after-forward (1 references)
target     prot opt source               destination         


Chain ufw-after-input (1 references)
target     prot opt source               destination         
ufw-skip-to-policy-input  udp  --  anywhere             anywhere             udp dpt:netbios-ns
ufw-skip-to-policy-input  udp  --  anywhere             anywhere             udp dpt:netbios-dgm
ufw-skip-to-policy-input  tcp  --  anywhere             anywhere             tcp dpt:netbios-ssn
ufw-skip-to-policy-input  tcp  --  anywhere             anywhere             tcp dpt:microsoft-ds
ufw-skip-to-policy-input  udp  --  anywhere             anywhere             udp dpt:bootps
ufw-skip-to-policy-input  udp  --  anywhere             anywhere             udp dpt:bootpc
ufw-skip-to-policy-input  all  --  anywhere             anywhere             ADDRTYPE match dst-type BROADCAST


Chain ufw-after-logging-forward (1 references)
target     prot opt source               destination         
LOG        all  --  anywhere             anywhere             limit: avg 3/min burst 10 LOG level warn prefix "[UFW BLOCK] "


Chain ufw-after-logging-input (1 references)
target     prot opt source               destination         
LOG        all  --  anywhere             anywhere             limit: avg 3/min burst 10 LOG level warn prefix "[UFW BLOCK] "


Chain ufw-after-logging-output (1 references)
target     prot opt source               destination         


Chain ufw-after-output (1 references)
target     prot opt source               destination         


Chain ufw-before-forward (1 references)
target     prot opt source               destination         
ACCEPT     all  --  anywhere             anywhere             ctstate RELATED,ESTABLISHED
ACCEPT     icmp --  anywhere             anywhere             icmp destination-unreachable
ACCEPT     icmp --  anywhere             anywhere             icmp time-exceeded
ACCEPT     icmp --  anywhere             anywhere             icmp parameter-problem
ACCEPT     icmp --  anywhere             anywhere             icmp echo-request
ufw-user-forward  all  --  anywhere             anywhere            


Chain ufw-before-input (1 references)
target     prot opt source               destination         
ACCEPT     all  --  anywhere             anywhere            
ACCEPT     all  --  anywhere             anywhere             ctstate RELATED,ESTABLISHED
ufw-logging-deny  all  --  anywhere             anywhere             ctstate INVALID
DROP       all  --  anywhere             anywhere             ctstate INVALID
ACCEPT     icmp --  anywhere             anywhere             icmp destination-unreachable
ACCEPT     icmp --  anywhere             anywhere             icmp time-exceeded
ACCEPT     icmp --  anywhere             anywhere             icmp parameter-problem
ACCEPT     icmp --  anywhere             anywhere             icmp echo-request
ACCEPT     udp  --  anywhere             anywhere             udp spt:bootps dpt:bootpc
ufw-not-local  all  --  anywhere             anywhere            
ACCEPT     udp  --  anywhere             mdns.mcast.net       udp dpt:mdns
ACCEPT     udp  --  anywhere             239.255.255.250      udp dpt:1900
ufw-user-input  all  --  anywhere             anywhere            


Chain ufw-before-logging-forward (1 references)
target     prot opt source               destination         


Chain ufw-before-logging-input (1 references)
target     prot opt source               destination         


Chain ufw-before-logging-output (1 references)
target     prot opt source               destination         


Chain ufw-before-output (1 references)
target     prot opt source               destination         
ACCEPT     all  --  anywhere             anywhere            
ACCEPT     all  --  anywhere             anywhere             ctstate RELATED,ESTABLISHED
ufw-user-output  all  --  anywhere             anywhere            


Chain ufw-logging-allow (0 references)
target     prot opt source               destination         
LOG        all  --  anywhere             anywhere             limit: avg 3/min burst 10 LOG level warn prefix "[UFW ALLOW] "


Chain ufw-logging-deny (2 references)
target     prot opt source               destination         
RETURN     all  --  anywhere             anywhere             ctstate INVALID limit: avg 3/min burst 10
LOG        all  --  anywhere             anywhere             limit: avg 3/min burst 10 LOG level warn prefix "[UFW BLOCK] "


Chain ufw-not-local (1 references)
target     prot opt source               destination         
RETURN     all  --  anywhere             anywhere             ADDRTYPE match dst-type LOCAL
RETURN     all  --  anywhere             anywhere             ADDRTYPE match dst-type MULTICAST
RETURN     all  --  anywhere             anywhere             ADDRTYPE match dst-type BROADCAST
ufw-logging-deny  all  --  anywhere             anywhere             limit: avg 3/min burst 10
DROP       all  --  anywhere             anywhere            


Chain ufw-reject-forward (1 references)
target     prot opt source               destination         


Chain ufw-reject-input (1 references)
target     prot opt source               destination         


Chain ufw-reject-output (1 references)
target     prot opt source               destination         


Chain ufw-skip-to-policy-forward (0 references)
target     prot opt source               destination         
DROP       all  --  anywhere             anywhere            


Chain ufw-skip-to-policy-input (7 references)
target     prot opt source               destination         
DROP       all  --  anywhere             anywhere            


Chain ufw-skip-to-policy-output (0 references)
target     prot opt source               destination         
ACCEPT     all  --  anywhere             anywhere            


Chain ufw-track-forward (1 references)
target     prot opt source               destination         


Chain ufw-track-input (1 references)
target     prot opt source               destination         


Chain ufw-track-output (1 references)
target     prot opt source               destination         
ACCEPT     tcp  --  anywhere             anywhere             ctstate NEW
ACCEPT     udp  --  anywhere             anywhere             ctstate NEW


Chain ufw-user-forward (1 references)
target     prot opt source               destination         


Chain ufw-user-input (1 references)
target     prot opt source               destination         
ACCEPT     tcp  --  anywhere             anywhere             tcp dpt:49999
ACCEPT     udp  --  anywhere             anywhere             udp dpt:49999
ACCEPT     tcp  --  anywhere             anywhere             tcp dpt:81
ACCEPT     udp  --  anywhere             anywhere             udp dpt:81
ACCEPT     tcp  --  anywhere             anywhere             tcp dpt:https
ACCEPT     udp  --  anywhere             anywhere             udp dpt:https
ACCEPT     tcp  --  anywhere             anywhere             tcp dpt:8124
ACCEPT     udp  --  anywhere             anywhere             udp dpt:8124


Chain ufw-user-limit (0 references)
target     prot opt source               destination         
LOG        all  --  anywhere             anywhere             limit: avg 3/min burst 5 LOG level warn prefix "[UFW LIMIT BLOCK] "
REJECT     all  --  anywhere             anywhere             reject-with icmp-port-unreachable


Chain ufw-user-limit-accept (0 references)
target     prot opt source               destination         
ACCEPT     all  --  anywhere             anywhere            


Chain ufw-user-logging-forward (0 references)
target     prot opt source               destination         


Chain ufw-user-logging-input (0 references)
target     prot opt source               destination         


Chain ufw-user-logging-output (0 references)
target     prot opt source               destination         


Chain ufw-user-output (1 references)
target     prot opt source               destination         



```

I tried both iptables and iptables-legacy...

My IP can still access my web server on 443 using NGINX as a reverse proxy on docker.

Why iptables is not banning that IP?

Thanks!!!

---

### Post by TheFu on 2023-10-26
Insert above the rules, not after.  Order matters.

---

### Post by sblantipodi on 2023-10-26
it seems that UFW and Docker doesn't work well... 
it's clear that ubuntu server is not a server distro :D

---

### Post by TheFu on 2023-10-26
> **sblantipodi said:**
> it seems that UFW and Docker doesn't work well... 
it's clear that ubuntu server is not a server distro :D

> It is a poor musician who blames his instrument.

[LIST]
[*]UFW is for end users, not servers that need more complex firewall controls. There are ways to tell UFW what you want. You can look those up just as easily as I can. [https://help.ubuntu.com/community/UFW](https://help.ubuntu.com/community/UFW) has examples and explanations.  If it doesn't work the way you think it should, perhaps the documentation is correct?  BTW, you mixed UFW and iptables.  That's an expert choice, so you are expected to use the tools in an expert manner, which seems reasonable.

[*]In Unix, anything can be a "server", so what is or isn't a server distro is extremely subjective.  If you don't like it. Feel free to try other distros.

[*] Nobody running a production server should be using a non-LTS release like 23.10.  They would be on 22.04 or 20.04 or waiting for 24.04+ a few months, say June 2024.  In the server realm, non-LTS are for testing and gaining understanding as packages and methods are modified in newer releases.

[*] With 22.04, nftables became available to replace iptables.  Might be smart to start using nftables for more advanced needs. If course, it is your choice.
[/LIST]

---

### Post by sblantipodi on 2023-10-26
> **TheFu said:**
> 
[LIST]
[*]UFW is for end users, not servers that need more complex firewall controls. There are ways to tell UFW what you want. You can look those up just as easily as I can. [https://help.ubuntu.com/community/UFW](https://help.ubuntu.com/community/UFW) has examples and explanations.  If it doesn't work the way you think it should, perhaps the documentation is correct?  BTW, you mixed UFW and iptables.  That's an expert choice, so you are expected to use the tools in an expert manner, which seems reasonable.
[*]In Unix, anything can be a "server", so what is or isn't a server distro is extremely subjective.  If you don't like it. Feel free to try other distros.
[*] Nobody running a production server should be using a non-LTS release like 23.10.  They would be on 22.04 or 20.04 or waiting for 24.04+ a few months, say June 2024.  In the server realm, non-LTS are for testing and gaining understanding as packages and methods are modified in newer releases.
[*] With 22.04, nftables became available to replace iptables.  Might be smart to start using nftables for more advanced needs. If course, it is your choice.
[/LIST]


UFW is just a wrapper around iptables and 23.04 uses nftables instead of iptables-legacy as default.
so, no, the problem still there but it's not an ubuntu problem it seems.

---

### Post by The Cog on 2023-10-26
I agree with TheFu. Mixing iptables commands with UFW commands is really complex, mainly because of the labyrinthine configuration that UFW uses. If you can't get UFW to do what you want by using UFW commands then it's time to look at nftables. Doing your own nftables rules from scratch will be much simpler than modifying UFW's iptables rules.

Bear in mind when testing that iptables/nftables/ufw only block new connections. Existing connections don't get broken by changing the rules after they were established.

---

### Post by sblantipodi on 2023-10-28
apart the obvious... 
is there a way to ban an IP on an ubuntu running nginx on docker?

---

### Post by TheFu on 2023-10-29
> **sblantipodi said:**
> apart the obvious... 
is there a way to ban an IP on an ubuntu running nginx on docker?

How do we know what you think is obvious?

First, in general, linux containers don't support kernel modules, unless they are setup in privileged mode.  That defeats 99.99999% of the reason why a contain would have security, so it shouldn't be done.  OTOH, I understand that is the default for docker for some reason. Perhaps that has changed.  I don't use docker and that was the key reason why not.

Second, you can block specific IPs or subnets using nginx. I do it all the  time.  I use an "include" statement so my blocks are centrally stored. An example:
```
  deny 110.184.0.0/8;
```

Third, if you setup docker using just a port forward and not a full network stack, you can use ufw to block a subnet, but the order of the rules matters. There are lots of examples for inserting a UFW rule above all other user-rules ... or you can manually add them to the settings under /etc/ufw/

Forth, you can insert an iptables rule into /etc/iptables/rules.v4 that goes above all INPUT rules to block what you need.  That's were I place my ipset rule.  ipset allows making thousands of IPs/subnets a single rule which exponentially speeds up processing. An example:
```
:ufw-user-output - [0:0]
[B]-A INPUT --match set --match-set countryblock  src --jump DROP
-A INPUT -p tcp -m tcp --dport 80 -m string --string "ZmEu" --algo bm --to 1000 -j DROP[/B]
-A INPUT -p tcp -m multiport --dports 80,443 -j f2b-wordpress

```

I added the bold lines. One to block everything in an ipset created as "countryblock" and the other was added when an abusive user-agent started visiting all my web properties.  Nginx can block based on reported user-agents too, BTW.  Agents with really old I.E. values are always scammers eating/stealing bandwidth, so I decided to block them completely.  Many VPS subnets are also blocked from services around the world due to abuse.  I think Azure was the first to be blocked, but I was already blocking all of MSFT's corporate networks after a few massive hacking and spamming attempts were launched from them in 2008.  Companies that cannot keep bad actors off their own systems, aren't trusted to visit mine.

If these things aren't working for you, please post your complete rules as proof. It is easy to do things incorrectly (like out of order).  I can't see the firewall not working correctly, so great claims of a bug required ironclad proof.

---

### Post by sblantipodi on 2023-10-30
it seems that putting the ban into the correct chain made the trick.

---

