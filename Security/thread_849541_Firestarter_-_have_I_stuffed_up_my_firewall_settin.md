---
title: "Firestarter - have I stuffed up my firewall settings?"
date: 2008-07-04
forum: Security
---

### Post by pedrogent on 2008-07-04
Hi folks.

I need to find out a bit about firewalls. I've read the man page for iptables (or at least skimmed over it) but it's a bit heavy for me.

Earlier today I experienced some very odd things happening on my desktop. I created a new document and all of a sudden many letter m's started appearing in the document title. A few other strange things were happening too like windows opening and closing.

I'm using firestarter. I may or may not have stuffed something up thru' mucking around with it. Also, the firestarter icon disappears from the taskbar after a while once I close the firestarter window. It seems strange that the icon would be there a while and then suddenly disappear.

I've been along to ShieldSUP! and everything seemed to be in order.

So I suppose what I want to know is: How can I check to make sure that my firewall is working properly?

Cheers.

---

### Post by kevdog on 2008-07-04
Do a 

sudo iptables -L

If you see more than just a default policy on the INPUT, OUTPUT, and FORWARD chains of ACCEPT, then your firewall is working.

---

### Post by pedrogent on 2008-07-04
Hi kevdog. Thanks for your assistance. I did 

```
sudo iptables -L
```

and it spat out a long list of stuff I don't understand. Things like DROP, ACCEPT, anywhere, etc. Is this a good thing or a bad thing?

I don't really know what 'more than just a default policy on the INPUT, OUTPUT, and FORWARD chains of ACCEPT' means. Could you possibly explain this a bit more?

---

### Post by kevdog on 2008-07-04
If you see a DROP statement or statements the firewall is active.  Again, packets can be ACCEPTED or allowed to pass or DROPPED and rejected, or FORWARDED if you are using internet connection sharing (which I don't think you use if you don't have another computer sharing your internet connection with two networking cards).  You are obviously filtering packets (ACCEPT vs DROP), so hence the firewall is active.  It would be easier if you posted your results so for example I could pick a couple of the lines and explain them.

---

### Post by pedrogent on 2008-07-04
Here it is...

```
Chain INPUT (policy DROP)
target     prot opt source               destination         
ACCEPT     tcp  --  192.168.1.1          anywhere            tcp flags:!FIN,SYN,RST,ACK/SYN 
ACCEPT     udp  --  192.168.1.1          anywhere            
ACCEPT     0    --  anywhere             anywhere            
ACCEPT     icmp --  anywhere             anywhere            limit: avg 10/sec burst 5 
DROP       0    --  anywhere             255.255.255.255     
DROP       0    --  anywhere             192.168.1.255       
DROP       0    --  BASE-ADDRESS.MCAST.NET/8  anywhere            
DROP       0    --  anywhere             BASE-ADDRESS.MCAST.NET/8 
DROP       0    --  255.255.255.255      anywhere            
DROP       0    --  anywhere             0.0.0.0             
DROP       0    --  anywhere             anywhere            state INVALID 
LSI        0    -f  anywhere             anywhere            limit: avg 10/min burst 5 
INBOUND    0    --  anywhere             anywhere            
LOG_FILTER  0    --  anywhere             anywhere            
LOG        0    --  anywhere             anywhere            LOG level info prefix `Unknown Input' 

Chain FORWARD (policy DROP)
target     prot opt source               destination         
ACCEPT     icmp --  anywhere             anywhere            limit: avg 10/sec burst 5 
LOG_FILTER  0    --  anywhere             anywhere            
LOG        0    --  anywhere             anywhere            LOG level info prefix `Unknown Forward' 

Chain OUTPUT (policy DROP)
target     prot opt source               destination         
ACCEPT     tcp  --  192.168.1.33         192.168.1.1         tcp dpt:domain 
ACCEPT     udp  --  192.168.1.33         192.168.1.1         udp dpt:domain 
ACCEPT     0    --  anywhere             anywhere            
DROP       0    --  BASE-ADDRESS.MCAST.NET/8  anywhere            
DROP       0    --  anywhere             BASE-ADDRESS.MCAST.NET/8 
DROP       0    --  255.255.255.255      anywhere            
DROP       0    --  anywhere             0.0.0.0             
DROP       0    --  anywhere             anywhere            state INVALID 
OUTBOUND   0    --  anywhere             anywhere            
LOG_FILTER  0    --  anywhere             anywhere            
LOG        0    --  anywhere             anywhere            LOG level info prefix `Unknown Output' 

Chain INBOUND (1 references)
target     prot opt source               destination         
ACCEPT     tcp  --  anywhere             anywhere            state RELATED,ESTABLISHED 
ACCEPT     udp  --  anywhere             anywhere            state RELATED,ESTABLISHED 
LSI        0    --  anywhere             anywhere            

Chain LOG_FILTER (5 references)
target     prot opt source               destination         

Chain LSI (2 references)
target     prot opt source               destination         
LOG_FILTER  0    --  anywhere             anywhere            
LOG        tcp  --  anywhere             anywhere            tcp flags:FIN,SYN,RST,ACK/SYN limit: avg 1/sec burst 5 LOG level info prefix `Inbound ' 
DROP       tcp  --  anywhere             anywhere            tcp flags:FIN,SYN,RST,ACK/SYN 
LOG        tcp  --  anywhere             anywhere            tcp flags:FIN,SYN,RST,ACK/RST limit: avg 1/sec burst 5 LOG level info prefix `Inbound ' 
DROP       tcp  --  anywhere             anywhere            tcp flags:FIN,SYN,RST,ACK/RST 
LOG        icmp --  anywhere             anywhere            icmp echo-request limit: avg 1/sec burst 5 LOG level info prefix `Inbound ' 
DROP       icmp --  anywhere             anywhere            icmp echo-request 
LOG        0    --  anywhere             anywhere            limit: avg 5/sec burst 5 LOG level info prefix `Inbound ' 
DROP       0    --  anywhere             anywhere            

Chain LSO (0 references)
target     prot opt source               destination         
LOG_FILTER  0    --  anywhere             anywhere            
LOG        0    --  anywhere             anywhere            limit: avg 5/sec burst 5 LOG level info prefix `Outbound ' 
REJECT     0    --  anywhere             anywhere            reject-with icmp-port-unreachable 

Chain OUTBOUND (1 references)
target     prot opt source               destination         
ACCEPT     icmp --  anywhere             anywhere            
ACCEPT     tcp  --  anywhere             anywhere            state RELATED,ESTABLISHED 
ACCEPT     udp  --  anywhere             anywhere            state RELATED,ESTABLISHED 
ACCEPT     0    --  anywhere             anywhere
```            

Thanks for your help with this.

---

### Post by kevdog on 2008-07-04
Who made the ruleset -- seems redundant

A few examples:

ACCEPT     icmp --  anywhere             anywhere            limit: avg 10/sec burst 5

Your accepting ping statements from any source but not more than 10/sec with no more than a burst of 5 in a row (5 in a second)


ACCEPT     0    --  anywhere             anywhere 

This seems to imply you are excepting all incoming connections.  However I doubt this is the case, b/c the proto is 0.


Chain LSI is your inbound logging utility.


Chain LOG_FILTER -- this does nothing -- I don't know why its even in there.

Chain OUTPUT:
DROP       0    --  anywhere             anywhere            state INVALID

Your dropping invalid outgoing packets (corrupt packets)

Who/How did you set up these rules and chains?

---

### Post by pedrogent on 2008-07-04
OK, this is making a bit more sense to me now.

I suppose firestarter set up the rules thru' its wizard. I certainly haven't made any manual changes myself. Is there a way I can make my rules/chains better/safer?

Yeah, I'm still confused...

---

### Post by kevdog on 2008-07-04
Firestarter does an adequate job.  Do you need more functionality than Firestarter?  Firestarter gives you basic functionality, but for most its adequate.  iptables has a lot more functionality then what is offered by firestarter, however for most people they don't need this extra functionality.  Again, match your needs to your tool.  Learning iptables is very difficult (I'm still doing it).  Its fun but does take a lot of practice and involves making mistakes.

---

### Post by pedrogent on 2008-07-04
OK well I guess all I need to know is that I haven't screwed up my firewall somehow and it appears that I haven't.

I will try and get my head around iptables one day but it looks very daunting.

I don't need mega-security mind you. I just was afraid that I may have screwed something up.

Thanks for all your help kevdog.

---

### Post by kevdog on 2008-07-04
There are a bunch of basic tutorials out there on the internet,  but you need to take time to read them.  One master reference site (not a good tutorial site) is:
[http://iptables-tutorial.frozentux.net/iptables-tutorial.html](http://iptables-tutorial.frozentux.net/iptables-tutorial.html)

A book about firewalls if you are interested in books is:
[http://www.cipherdyne.org/LinuxFirewalls/](http://www.cipherdyne.org/LinuxFirewalls/)

---

