---
title: "cannot connect to port number when firewall is enabled"
date: 2010-09-05
forum: Security
---

### Post by stevestark on 2010-09-05
i am using 9.10 karmic. Firewall is enabled. added ports with ufw allow [portnumber], and i still cannot connect to a port number. iv tryed ufw allow ssh/tcp but that does not work. the ports work when i disable the firewall and i dont want to do that. your help is appreciated.

> Why is the ufw firewall not enabled by default? 

ufw is available in all new installations of Ubuntu since 8.04 LTS, but is disabled by default. The standard Ubuntu installation has a no open service ports policy, so enabling the firewall by default doesn't gain any extra security in the default installation, but could provide confusion for people new to Ubuntu when new software that is installed does not work because of restrictive firewall rules. As a result, when first adding ufw to Ubuntu it was decided that users must 'opt-in' to using the firewall. In Ubuntu 9.04 and later, you can enable ufw during installation using preseeding. See /usr/share/doc/ufw/README.Debian for details.

[https://wiki.ubuntu.com/SecurityTeam/FAQ?action=fullsearch&context=180&value=firewall+port&titlesearch=Titles](https://wiki.ubuntu.com/SecurityTeam/FAQ?action=fullsearch&context=180&value=firewall+port&titlesearch=Titles)

is the above saying that i dont need a firewall enabled and that the ports are disabled by default?

---

### Post by The Cog on 2010-09-05
> **stevestark said:**
> 
is the above saying that i dont need a firewall enabled and that the ports are disabled by default?

Yes it is. 

If you want to keep the firewall enabled, perhaps getting a trace with wireshark would help. It will confirm exactly what's happening and show if any other ports are also needed to be opened for secondary connections.

---

### Post by cdenley on 2010-09-05
> **The Cog said:**
> Yes it is. 

If you want to keep the firewall enabled, perhaps getting a trace with wireshark would help. It will confirm exactly what's happening and show if any other ports are also needed to be opened for secondary connections.

They are "disabled" in the sense that there is nothing significant listening on any ports so your system wouldn't accept any connections. Why filter connections no applications are going to accept anyway?

If you really want to solve this problem, I would post your iptables rules. Have you configured another firewall tool, such as firestarter, which is configuring iptables to filter traffic regardless of your UFW rules?
```

sudo iptables -L -n

```

---

### Post by stevestark on 2010-09-05
> If you really want to solve this problem, I would post your iptables rules. Have you configured another firewall tool, such as firestarter, which is configuring iptables to filter traffic regardless of your UFW rules?


it seems that when the firewall is disabled, i am able to connect to any port. when the firewall is enabled, i am not able to connect to any port. i have tried firestarter and that program has not help me much. i am not able to open a port or dont know how in firestarter. is there another program that i can try?

edit: here are the iptable rules when firewall is disabled

Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination

---

### Post by BkkBonanza on 2010-09-05
It would be more helpful to have the iptables listing when the firewall is enabled since that is when you have the problem. 
When it's disabled there is no problem, so nothing to fix.

---

### Post by bodhi.zazen on 2010-09-05
> **stevestark said:**
> i am using 9.10 karmic. Firewall is enabled. added ports with ufw allow [portnumber], and i still cannot connect to a port number. iv tryed ufw allow ssh/tcp but that does not work. the ports work when i disable the firewall and i dont want to do that. your help is appreciated.

You need to provide more information.

What port ?

On a LAN or from the internet ? If from the internet, did you forward your port ?

What are your rules ?

---

### Post by stevestark on 2010-09-06
> **bodhi.zazen said:**
> You need to provide more information.

What port ?

On a LAN or from the internet ? If from the internet, did you forward your port ?

What are your rules ?

on my lan, i cant connect to port 50000 or 80 or any port.
here are the iptable rules when firewall is enabled


> Chain INPUT (policy DROP)
target     prot opt source               destination         
ufw-before-logging-input  all  --  0.0.0.0/0            0.0.0.0/0           
ufw-before-input  all  --  0.0.0.0/0            0.0.0.0/0           
ufw-after-input  all  --  0.0.0.0/0            0.0.0.0/0           
ufw-after-logging-input  all  --  0.0.0.0/0            0.0.0.0/0           
ufw-reject-input  all  --  0.0.0.0/0            0.0.0.0/0           
ufw-track-input  all  --  0.0.0.0/0            0.0.0.0/0           

Chain FORWARD (policy DROP)
target     prot opt source               destination         
ufw-before-logging-forward  all  --  0.0.0.0/0            0.0.0.0/0           
ufw-before-forward  all  --  0.0.0.0/0            0.0.0.0/0           
ufw-after-forward  all  --  0.0.0.0/0            0.0.0.0/0           
ufw-after-logging-forward  all  --  0.0.0.0/0            0.0.0.0/0           
ufw-reject-forward  all  --  0.0.0.0/0            0.0.0.0/0           

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination         
ufw-before-logging-output  all  --  0.0.0.0/0            0.0.0.0/0           
ufw-before-output  all  --  0.0.0.0/0            0.0.0.0/0           
ufw-after-output  all  --  0.0.0.0/0            0.0.0.0/0           
ufw-after-logging-output  all  --  0.0.0.0/0            0.0.0.0/0           
ufw-reject-output  all  --  0.0.0.0/0            0.0.0.0/0           
ufw-track-output  all  --  0.0.0.0/0            0.0.0.0/0           

Chain ufw-after-forward (1 references)
target     prot opt source               destination         

Chain ufw-after-input (1 references)
target     prot opt source               destination         
RETURN     udp  --  0.0.0.0/0            0.0.0.0/0           udp dpt:137 
RETURN     udp  --  0.0.0.0/0            0.0.0.0/0           udp dpt:138 
RETURN     tcp  --  0.0.0.0/0            0.0.0.0/0           tcp dpt:139 
RETURN     tcp  --  0.0.0.0/0            0.0.0.0/0           tcp dpt:445 
RETURN     udp  --  0.0.0.0/0            0.0.0.0/0           udp dpt:67 
RETURN     udp  --  0.0.0.0/0            0.0.0.0/0           udp dpt:68 
RETURN     all  --  0.0.0.0/0            0.0.0.0/0           ADDRTYPE match dst-type BROADCAST 

Chain ufw-after-logging-forward (1 references)
target     prot opt source               destination         
LOG        all  --  0.0.0.0/0            0.0.0.0/0           limit: avg 3/min burst 10 LOG flags 0 level 4 prefix `[UFW BLOCK] ' 

Chain ufw-after-logging-input (1 references)
target     prot opt source               destination         
LOG        all  --  0.0.0.0/0            0.0.0.0/0           limit: avg 3/min burst 10 LOG flags 0 level 4 prefix `[UFW BLOCK] ' 

Chain ufw-after-logging-output (1 references)
target     prot opt source               destination         

Chain ufw-after-output (1 references)
target     prot opt source               destination         

Chain ufw-before-forward (1 references)
target     prot opt source               destination         
ufw-user-forward  all  --  0.0.0.0/0            0.0.0.0/0           

Chain ufw-before-input (1 references)
target     prot opt source               destination         
ACCEPT     all  --  0.0.0.0/0            0.0.0.0/0           
ACCEPT     all  --  0.0.0.0/0            0.0.0.0/0           state RELATED,ESTABLISHED 
ufw-logging-deny  all  --  0.0.0.0/0            0.0.0.0/0           state INVALID 
DROP       all  --  0.0.0.0/0            0.0.0.0/0           state INVALID 
ACCEPT     icmp --  0.0.0.0/0            0.0.0.0/0           icmp type 3 
ACCEPT     icmp --  0.0.0.0/0            0.0.0.0/0           icmp type 4 
ACCEPT     icmp --  0.0.0.0/0            0.0.0.0/0           icmp type 11 
ACCEPT     icmp --  0.0.0.0/0            0.0.0.0/0           icmp type 12 
ACCEPT     icmp --  0.0.0.0/0            0.0.0.0/0           icmp type 8 
ACCEPT     udp  --  0.0.0.0/0            0.0.0.0/0           udp spt:67 dpt:68 
ufw-not-local  all  --  0.0.0.0/0            0.0.0.0/0           
ACCEPT     all  --  224.0.0.0/4          0.0.0.0/0           
ACCEPT     all  --  0.0.0.0/0            224.0.0.0/4         
ufw-user-input  all  --  0.0.0.0/0            0.0.0.0/0           

Chain ufw-before-logging-forward (1 references)
target     prot opt source               destination         

Chain ufw-before-logging-input (1 references)
target     prot opt source               destination         

Chain ufw-before-logging-output (1 references)
target     prot opt source               destination         

Chain ufw-before-output (1 references)
target     prot opt source               destination         
ACCEPT     all  --  0.0.0.0/0            0.0.0.0/0           
ACCEPT     all  --  0.0.0.0/0            0.0.0.0/0           state RELATED,ESTABLISHED 
ufw-user-output  all  --  0.0.0.0/0            0.0.0.0/0           

Chain ufw-logging-allow (0 references)
target     prot opt source               destination         
LOG        all  --  0.0.0.0/0            0.0.0.0/0           limit: avg 3/min burst 10 LOG flags 0 level 4 prefix `[UFW ALLOW] ' 

Chain ufw-logging-deny (2 references)
target     prot opt source               destination         
LOG        all  --  0.0.0.0/0            0.0.0.0/0           limit: avg 3/min burst 10 LOG flags 0 level 4 prefix `[UFW BLOCK] ' 

Chain ufw-not-local (1 references)
target     prot opt source               destination         
RETURN     all  --  0.0.0.0/0            0.0.0.0/0           ADDRTYPE match dst-type LOCAL 
RETURN     all  --  0.0.0.0/0            0.0.0.0/0           ADDRTYPE match dst-type MULTICAST 
RETURN     all  --  0.0.0.0/0            0.0.0.0/0           ADDRTYPE match dst-type BROADCAST 
ufw-logging-deny  all  --  0.0.0.0/0            0.0.0.0/0           limit: avg 3/min burst 10 
DROP       all  --  0.0.0.0/0            0.0.0.0/0           

Chain ufw-reject-forward (1 references)
target     prot opt source               destination         

Chain ufw-reject-input (1 references)
target     prot opt source               destination         

Chain ufw-reject-output (1 references)
target     prot opt source               destination         

Chain ufw-track-input (1 references)
target     prot opt source               destination         

Chain ufw-track-output (1 references)
target     prot opt source               destination         
ACCEPT     tcp  --  0.0.0.0/0            0.0.0.0/0           state NEW 
ACCEPT     udp  --  0.0.0.0/0            0.0.0.0/0           state NEW 

Chain ufw-user-forward (1 references)
target     prot opt source               destination         

Chain ufw-user-input (1 references)
target     prot opt source               destination         
ACCEPT     tcp  --  0.0.0.0/0            0.0.0.0/0           tcp dpt:50000 
ACCEPT     udp  --  0.0.0.0/0            0.0.0.0/0           udp dpt:50000 

Chain ufw-user-limit (0 references)
target     prot opt source               destination         
LOG        all  --  0.0.0.0/0            0.0.0.0/0           limit: avg 3/min burst 5 LOG flags 0 level 4 prefix `[UFW LIMIT BLOCK] ' 
REJECT     all  --  0.0.0.0/0            0.0.0.0/0           reject-with icmp-port-unreachable 

Chain ufw-user-limit-accept (0 references)
target     prot opt source               destination         
ACCEPT     all  --  0.0.0.0/0            0.0.0.0/0           

Chain ufw-user-logging-forward (0 references)
target     prot opt source               destination         

Chain ufw-user-logging-input (0 references)
target     prot opt source               destination         

Chain ufw-user-logging-output (0 references)
target     prot opt source               destination         

Chain ufw-user-output (1 references)
target     prot opt source               destination  

---

### Post by BkkBonanza on 2010-09-06
Have a look at the log to see what is showing up when you try to connect,

cat /var/log/messages | grep UFW

I'm not sure what UFW usually has for rules but doesn't "limit: avg 3/min" seem like a very low limit?

---

