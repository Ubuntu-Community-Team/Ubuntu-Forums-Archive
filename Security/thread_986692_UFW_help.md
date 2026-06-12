---
title: "UFW help"
date: 2008-11-18
forum: Security
---

### Post by brandon88tube on 2008-11-18
I just started using UFW and I can't figure out if its working properly because I set the default to deny and I enabled logging, but I can't find a single trace of UFW in the log files anywhere. I'm also able to use Pidgin etc. so I don't know if it is truly denying stuff.

---

### Post by bodhi.zazen on 2008-11-19
You can check your rules with sudo iptables -L

so ...

```
sudo ufw enable
sudo ufw default deny
```

List your iptables settings with :

```
sudo iptables -L
```

UFW logs to syslog, so ...

tail syslog

or , better :

```
grep UFW /var/log/syslog | less
```

---

### Post by brandon88tube on 2008-11-19
> **bodhi.zazen said:**
> You can check your rules with sudo iptables -L

so ...

```
sudo ufw enable
sudo ufw default deny
```

List your iptables settings with :

```
sudo iptables -L
```

Ok, I did that, but I am lost. Here is the output.```
Chain INPUT (policy DROP)
target     prot opt source               destination         
ufw-before-input  all  --  anywhere             anywhere            
ufw-after-input  all  --  anywhere             anywhere            

Chain FORWARD (policy DROP)
target     prot opt source               destination         
ufw-before-forward  all  --  anywhere             anywhere            
ufw-after-forward  all  --  anywhere             anywhere            

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination         
ufw-before-output  all  --  anywhere             anywhere            
ufw-after-output  all  --  anywhere             anywhere            

Chain ufw-after-forward (1 references)
target     prot opt source               destination         
LOG        all  --  anywhere             anywhere            limit: avg 3/min burst 10 LOG level warning prefix `[UFW BLOCK FORWARD]: ' 
RETURN     all  --  anywhere             anywhere            

Chain ufw-after-input (1 references)
target     prot opt source               destination         
RETURN     udp  --  anywhere             anywhere            udp dpt:netbios-ns 
RETURN     udp  --  anywhere             anywhere            udp dpt:netbios-dgm 
RETURN     tcp  --  anywhere             anywhere            tcp dpt:netbios-ssn 
RETURN     tcp  --  anywhere             anywhere            tcp dpt:microsoft-ds 
RETURN     udp  --  anywhere             anywhere            udp dpt:bootps 
RETURN     udp  --  anywhere             anywhere            udp dpt:bootpc 
RETURN     all  --  anywhere             anywhere            ADDRTYPE match dst-type BROADCAST 
LOG        all  --  anywhere             anywhere            limit: avg 3/min burst 10 LOG level warning prefix `[UFW BLOCK INPUT]: ' 
RETURN     all  --  anywhere             anywhere            

Chain ufw-after-output (1 references)
target     prot opt source               destination         
RETURN     all  --  anywhere             anywhere            

Chain ufw-before-forward (1 references)
target     prot opt source               destination         
ufw-user-forward  all  --  anywhere             anywhere            
RETURN     all  --  anywhere             anywhere            

Chain ufw-before-input (1 references)
target     prot opt source               destination         
ACCEPT     all  --  anywhere             anywhere            
ACCEPT     all  --  anywhere             anywhere            ctstate RELATED,ESTABLISHED 
DROP       all  --  anywhere             anywhere            ctstate INVALID 
ACCEPT     icmp --  anywhere             anywhere            icmp destination-unreachable 
ACCEPT     icmp --  anywhere             anywhere            icmp source-quench 
ACCEPT     icmp --  anywhere             anywhere            icmp time-exceeded 
ACCEPT     icmp --  anywhere             anywhere            icmp parameter-problem 
ACCEPT     icmp --  anywhere             anywhere            icmp echo-request 
ACCEPT     udp  --  anywhere             anywhere            udp spt:bootps dpt:bootpc 
ufw-not-local  all  --  anywhere             anywhere            
ACCEPT     all  --  BASE-ADDRESS.MCAST.NET/4  anywhere            
ACCEPT     all  --  anywhere             BASE-ADDRESS.MCAST.NET/4 
ufw-user-input  all  --  anywhere             anywhere            
RETURN     all  --  anywhere             anywhere            

Chain ufw-before-output (1 references)
target     prot opt source               destination         
ACCEPT     all  --  anywhere             anywhere            
ACCEPT     tcp  --  anywhere             anywhere            state NEW,RELATED,ESTABLISHED 
ACCEPT     udp  --  anywhere             anywhere            state NEW,RELATED,ESTABLISHED 
ufw-user-output  all  --  anywhere             anywhere            
RETURN     all  --  anywhere             anywhere            

Chain ufw-not-local (1 references)
target     prot opt source               destination         
RETURN     all  --  anywhere             anywhere            ADDRTYPE match dst-type LOCAL 
RETURN     all  --  anywhere             anywhere            ADDRTYPE match dst-type MULTICAST 
RETURN     all  --  anywhere             anywhere            ADDRTYPE match dst-type BROADCAST 
LOG        all  --  anywhere             anywhere            limit: avg 3/min burst 10 LOG level warning prefix `[UFW BLOCK NOT-TO-ME]: ' 
DROP       all  --  anywhere             anywhere            

Chain ufw-user-forward (1 references)
target     prot opt source               destination         
RETURN     all  --  anywhere             anywhere            

Chain ufw-user-input (1 references)
target     prot opt source               destination         
RETURN     all  --  anywhere             anywhere            

Chain ufw-user-limit (0 references)
target     prot opt source               destination         
LOG        all  --  anywhere             anywhere            limit: avg 3/min burst 5 LOG level warning prefix `[UFW LIMIT]: ' 
REJECT     all  --  anywhere             anywhere            reject-with icmp-port-unreachable 

Chain ufw-user-limit-accept (0 references)
target     prot opt source               destination         
ACCEPT     all  --  anywhere             anywhere            

Chain ufw-user-output (1 references)
target     prot opt source               destination         
RETURN     all  --  anywhere             anywhere     
```

---

### Post by bodhi.zazen on 2008-11-19
That output looks fine. The most important line is the one with "DROP" in it.

UFW (iptables) will not block conntections you initiate, only incoming connections.

You can port scan your box if you wish.

nmap -v -A ipaddress (you need to do this from a remote box).

---

### Post by brandon88tube on 2008-11-19
> **bodhi.zazen said:**
> That output looks fine. The most important line is the one with "DROP" in it.

UFW (iptables) will not block conntections you initiate, only incoming connections.

You can port scan your box if you wish.

nmap -v -A ipaddress (you need to do this from a remote box).

Wouldn't that just scan my router and not my laptop?

---

### Post by bodhi.zazen on 2008-11-19
> **brandon88tube said:**
> Wouldn't that just scan my router and not my laptop?

Well yes if you scan your Public IP address it will.

But if you scan your laptop from another box on your lan using your private ip address it will port scan the laptop.

You can not scan the laptop from the laptop.

---

### Post by brandon88tube on 2008-11-19
Well, I can't really do the nmap on my laptop then. Don't have another computer on the same network I trust to use. Also they are Windows machines.

---

