---
title: "Uncomplicated Firewall"
date: 2008-07-02
forum: Security
---

### Post by keithvella on 2008-07-02
I made several attempts at using the ufw interface to modify iptables rules. This seems to be working properly, i.e. iptables -L -n indicates that the rules are being modified by ufw. The problem is that the iptables rules are not being applied to the network interfaces (both wired and wireless). This behaviour can be replicated when booting off the live cd. I tried using webmin to modify the iptables rules instead with better results.

---

### Post by cdenley on 2008-07-02
> **keithvella said:**
> The problem is that the iptables rules are not being applied to the network interfaces (both wired and wireless).

How did you determine this?

---

### Post by keithvella on 2008-07-02
I created a rule which denies 80/tcp and 80/udp from any source. I tried to browse the web and found that this is possible. This led me to think that the rules are not being applied properly.

---

### Post by cdenley on 2008-07-02
> **keithvella said:**
> I created a rule which denies 80/tcp and 80/udp from any source. I tried to browse the web and found that this is possible. This led me to think that the rules are not being applied properly.

I don't think UFW filters outgoing traffic or established connections. This rule will prevent someone else from connecting to a server running on your computer using port 80.

---

### Post by kevdog on 2008-07-02
How did you create your rules?  Can you list

sudo iptables -L

---

### Post by keithvella on 2008-07-03
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
DROP       tcp  --  anywhere             anywhere            tcp dpt:www 
DROP       udp  --  anywhere             anywhere            udp dpt:www 
RETURN     all  --  anywhere             anywhere            

Chain ufw-user-output (1 references)
target     prot opt source               destination         
RETURN     all  --  anywhere             anywhere

---

### Post by kevdog on 2008-07-03
So here are the chains you created:

Chain ufw-user-input (1 references)
target prot opt source destination
DROP tcp -- anywhere anywhere tcp dpt:www
DROP udp -- anywhere anywhere udp dpt:www
RETURN all -- anywhere anywhere

Chain ufw-user-output (1 references)
target prot opt source destination
RETURN all -- anywhere anywhere

Its only blocking incoming connections on port 80.  No outgoing connections are blocked.  Usually when you connect via the web to a remote port 80 port, its a much higher port number locally used to initiate the connection that sends packets to a remote port 80.  You can block outgoing connections to a remote port 80 by filtering by the destination port number rather than the source port number and adding this to the output chain or ufw-user-output chain.

---

### Post by keithvella on 2008-07-04
Many thanks for your reply. Wouldn't egress traffic also be an incoming connection with destination port 80 (with respect to the locally defined interfaces)? I appreciate the difference between source ports and destination ports. Note that it is also possible to block outgoing traffic by adding rules to the input chain but maybe this is not the intended way of achieving this objective.

---

### Post by kevdog on 2008-07-04
So I can understand your situation better, can you just reiterate what you are trying to accomplish or what access you are trying to filter/limit?

---

### Post by keithvella on 2008-07-10
What I would have wanted to achieve with ufw is to control egress traffic from my machine. I am in the process of carrying out a behavioural analysis of a Windows XP (virtual) machine installed as a guest in VirtualBox after I purposely infect it with malware. I am using NAT to share the network connection available to the host with the guest machine. Due to the nature of what I am trying to do, I would like to control the destination IPs and ports available to the guest by implementing an egress filter on the host. I hope that this clarifies matters.

---

### Post by kevdog on 2008-07-10
So it sounds like you want to block outgoing connections that would connect to a remote port 80 (http).  

So something like this would do:

sudo iptables -A OUTPUT -m state --state INVALID -j DROP
sudo iptables -A OUTPUT -m state --state ESTABLISHED,RELATED -j ACCEPT
sudo iptables -A OUTPUT -p tcp --dport 80 --syn -m state --state NEW -j DROP

So basically any outgoing new local connection attempting to connect to a remote port 80 will be dropped.  This however will prevent you from accessing the internet (most web browsing).  Is this what you want?

---

