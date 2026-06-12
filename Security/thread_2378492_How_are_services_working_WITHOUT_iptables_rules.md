---
title: "How are services working WITHOUT iptables rules"
date: 2017-11-23
forum: Security
---

### Post by wintermute0002 on 2017-11-23
I am running a bunch of services, containers and VMs in my lab server. I haven't made iptables rules for all of them but they all work... 

e.g. I haven't opened ports for SMB or NFS but they work. 

Also, just wanted to clarify, assuming iptables is working (!?!?!), the rules in the DOCKER chain - they only allow packets with destination IP of the docker virtual networks correct? not my 'real' NIC?

What gives?!?!?

```
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         
ACCEPT     udp  --  anywhere             anywhere             udp dpt:domain
ACCEPT     tcp  --  anywhere             anywhere             tcp dpt:domain
ACCEPT     udp  --  anywhere             anywhere             udp dpt:bootps
ACCEPT     tcp  --  anywhere             anywhere             tcp dpt:bootps
f2b-sshd   tcp  --  anywhere             anywhere             multiport dports ssh
ACCEPT     tcp  --  anywhere             anywhere             tcp dpt:8000
ACCEPT     tcp  --  anywhere             anywhere             tcp dpt:8001
ACCEPT     tcp  --  anywhere             anywhere             tcp dpt:5900
ACCEPT     tcp  --  anywhere             anywhere             tcp dpt:5901
ACCEPT     tcp  --  anywhere             anywhere             tcp dpt:5902
ACCEPT     tcp  --  anywhere             anywhere             tcp dpt:5903
ACCEPT     tcp  --  anywhere             anywhere             tcp dpt:5904
ACCEPT     tcp  --  anywhere             anywhere             tcp dpt:5905
ACCEPT     tcp  --  anywhere             anywhere             tcp dpt:5906
ACCEPT     tcp  --  anywhere             anywhere             tcp dpt:5907
ACCEPT     tcp  --  anywhere             anywhere             tcp dpt:5908
ACCEPT     tcp  --  anywhere             anywhere             tcp dpt:webmin
ACCEPT     tcp  --  anywhere             anywhere             tcp dpt:smtp
ACCEPT     tcp  --  anywhere             anywhere             tcp dpt:smtp
ACCEPT     udp  --  anywhere             anywhere             udp dpt:domain


Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         
ACCEPT     all  --  anywhere             192.168.122.0/24     ctstate RELATED,ESTABLISHED
ACCEPT     all  --  192.168.122.0/24     anywhere            
ACCEPT     all  --  anywhere             anywhere            
REJECT     all  --  anywhere             anywhere             reject-with icmp-port-unreachable
REJECT     all  --  anywhere             anywhere             reject-with icmp-port-unreachable
DOCKER-USER  all  --  anywhere             anywhere            
DOCKER-ISOLATION  all  --  anywhere             anywhere            
ACCEPT     all  --  anywhere             anywhere             ctstate RELATED,ESTABLISHED
DOCKER     all  --  anywhere             anywhere            
ACCEPT     all  --  anywhere             anywhere            
ACCEPT     all  --  anywhere             anywhere            


Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination         
ACCEPT     udp  --  anywhere             anywhere             udp dpt:bootpc


Chain DOCKER (1 references)
target     prot opt source               destination         
ACCEPT     udp  --  anywhere             172.17.0.2           udp dpt:openvpn
ACCEPT     tcp  --  anywhere             172.17.0.3           tcp dpt:8888
ACCEPT     tcp  --  anywhere             172.17.0.3           tcp dpt:55555
ACCEPT     tcp  --  anywhere             172.17.0.5           tcp dpt:smtp
ACCEPT     tcp  --  anywhere             172.17.0.4           tcp dpt:http-alt
ACCEPT     udp  --  anywhere             172.17.0.4           udp dpt:domain


Chain DOCKER-ISOLATION (1 references)
target     prot opt source               destination         
RETURN     all  --  anywhere             anywhere            


Chain DOCKER-USER (1 references)
target     prot opt source               destination         
RETURN     all  --  anywhere             anywhere            


Chain f2b-sshd (1 references)
target     prot opt source               destination         
REJECT     all  --  181.214.87.4         anywhere             reject-with icmp-port-unreachable
RETURN     all  --  anywhere             anywhere            

```

---

### Post by SeijiSensei on 2017-11-24
I don't see any default REJECT rule at the bottom of the INPUT chain. Since the default INPUT policy is ACCEPT, all packets will be accepted even if they don't match any rules.

The last line of my INPUT rulesets:
```

iptables -A INPUT -j REJECT --reject-with icmp-host-prohibited

```

---

### Post by wintermute0002 on 2017-11-26
DOH

I feel so stupid.... 

But at the same time, why isn't one there? Is it because my iptables likely got initialised with docker + fail2ban? Ubuntu server is off by default right?

I guess this is actually fine for my use-case as the only port I have NAT is SSH which is going through fail2ban chain? I don't actually WANT to filter internally, though I suppose it is best practice.

---

### Post by The Cog on 2017-11-26
A default install has no iptables rules. It lets everything through. Unless you add some rules to block stuff then it won't be blocked. Adding rules that allow stuff that's already allowed doesn't achieve anything. 

I think that docker adds a bunch of rules when it's started to allow stuff through. But if you're not blocking anything in the first place then these extra rules are harmless (although perhaps misleading in that they are just ineffectual "noise"). 

If you want to block stuff then by all means change the default policy to DROP. Then your computer won't work until you add extra rules to unblock thigs again. Docker anticipates this problem and automatically adds some rules to allow stuff without your having to spend a while wondering why nothing works.

---

