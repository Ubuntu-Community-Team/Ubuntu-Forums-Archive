---
title: "port state Filtered service HTTP server ubuntu 16.04"
date: 2021-03-29
forum: Security
---

### Post by hicks71 on 2021-03-29
[SIZE=2][FONT=arial]Hi Comunity:
  
   I want to do the following query.  I have a server that is in the cloud, and in the iptables configuration, I have the port 80 open, but I can't show the apache service. [/FONT][/SIZE][SIZE=2][FONT=arial]I scan the port and it tells me that it is in a Filter state.
  Is there any other configuration that I should check why the port is being filtered?

Iptables:

-A INPUT -m state --state RELATED,ESTABLISHED -j ACCEPT
-A INPUT -p icmp -j ACCEPT
-A INPUT -i lo -j ACCEPT
-A INPUT -p udp -m udp --sport 123 -j ACCEPT
-A INPUT -p tcp -m state --state NEW -m tcp --dport 22 -j ACCEPT
-A INPUT -j REJECT --reject-with icmp-host-prohibited
-A INPUT -p tcp -m state --state NEW -m tcp --dport 80 -j ACCEPT
-A OUTPUT -p tcp -m state --state NEW -m tcp --dport 80 -j ACCEPT
-A INPUT -p tcp -m state --state NEW -m tcp --dport 5000 -j ACCEPT
-A OUTPUT -p tcp -m state --state NEW -m tcp --dport 5000 -j ACCEPT
-A FORWARD -j REJECT --reject-with icmp-host-prohibited


nmap:

PORT   STATE    SERVICE
80/tcp filtered http

thank you very much.[/FONT][/SIZE]

---

### Post by Doug S on 2021-03-30
You have not showed us enough information, nor formatted it properly. We need to also see your default policies for the chains. After you have tried to access port 80, do "sudo iptables -xvnL" and show us the results. Anyway, your rules order is incorrect, and you will never get to to your port 80 ACCEPT rule in your INPUT chain. It needs to be before your REJECT line. There may be other issues if your default OUTPUT policy is DROP.

---

### Post by SeijiSensei on 2021-03-30
As Doug says, the rule
```
-A INPUT -j REJECT --reject-with icmp-host-prohibited
```
must come at the end of all INPUT statements.  Order matters greatly in iptables.  Also if you want to block forwarding there are other options.  This uses an iptables "policy."

```

-P INPUT ACCEPT
-P FORWARD DROP
-P OUTPUT ACCEPT

-A INPUT -m state --state RELATED,ESTABLISHED -j ACCEPT
-A INPUT -p icmp -j ACCEPT
-A INPUT -i lo -j ACCEPT
-A INPUT -p udp -m udp --sport 123 -j ACCEPT
-A INPUT -p tcp -m state --state NEW -m tcp --dport 22 -j ACCEPT
-A INPUT -p tcp -m state --state NEW -m tcp --dport 80 -j ACCEPT
-A INPUT -p tcp -m state --state NEW -m tcp --dport 5000 -j ACCEPT
-A INPUT -j REJECT --reject-with icmp-host-prohibited

```
I don't see much reason to control the OUTPUT chain so I just use ACCEPT. I'm actually unclear on why you have those OUTPUT directives at all.

By default, packet forwarding across interfaces is disabled in Ubuntu, so the FORWARD policy is redundant. For details, read the discussion in the file /etc/sysctl.conf concerning the "net.ipv4.ip_forward=1" directive.

---

### Post by Doug S on 2021-03-30
> **SeijiSensei said:**
> I don't see much reason to control the OUTPUT chain so I just use ACCEPT. I'm actually unclear on why you have those OUTPUT directives at all.

Hi Seiji,

Thanks for your better, more thorough, reply than mine.
I use a default policy of DROP on the OUTPUT chain merely to be certain than I have thought of everything and never actually hit the rule.
In reality, and because I do sometimes reload my complicated rule set via script on the fly the default does get some hits. Example:

```
Chain OUTPUT (policy DROP 12 packets, 1536 bytes)
    pkts      bytes target     prot opt in     out     source               destination
    2727   142133 ACCEPT     all  --  *      lo      0.0.0.0/0            0.0.0.0/0
       0        0 ACCEPT     all  --  *      br0     XXX.XXX.XXX.XXX      192.168.111.0/24
  419392 129880156 ACCEPT     all  --  *      br0     192.168.111.1        192.168.111.0/24
  797421 108912037 ACCEPT     all  --  *      enp1s0  XXX.XXX.XXX.XXX     0.0.0.0/0
       0        0 LOG        all  --  *      *       0.0.0.0/0            0.0.0.0/0            LOG flags 0 level 6 prefix "OCATCH:"
       0        0 DROP       all  --  *      *       0.0.0.0/0            0.0.0.0/0

```

---

### Post by hicks71 on 2021-03-30
I moved the rules above REJECT and now the ports are open

thank you very much [ 						 							[IMG]https://ubuntuforums.org/customavatars/avatar1245983_2.gif[/IMG] 						 					]("https://ubuntuforums.org/member.php?u=1245983") 				 				 					 						 	[**[COLOR=#DD4814][B]Doug S**[/COLOR][/B]]("https://ubuntuforums.org/member.php?u=1245983") .

---

