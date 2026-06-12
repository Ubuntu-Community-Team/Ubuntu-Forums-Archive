---
title: "Can't access secure sites."
date: 2009-12-29
forum: Security
---

### Post by PDA1 on 2009-12-29
I can't log in to or access any website that has a "https"  in its address.  I get the dreaded Unable to Connect screen.

I'm using Firefox (Shiretoko) and Ubunut 9.10

The same problem happens if I use Konqueror.

The problem doesn't happen if I use another one of my computers, like my desktop.

I've tried uninstalling and then re-installing Firefox but the same trouble happens.

How do I fix this?

---

### Post by Sarmacid on 2009-12-29
Did you set up a firewall in your pc? Https uses port 443 instead of 80, so you'll need to allow it if you got a firewall.

---

### Post by CharlesA on 2009-12-29
> **Sarmacid said:**
> Did you set up a firewall in your pc? Https uses port 443 instead of 80, so you'll need to allow it if you got a firewall.

This. I had the same problem after "locking down" my firewall.

---

### Post by PDA1 on 2009-12-29
I don't know how to lock down a firewall and don't even know if I have one.

Ubuntu is new to me so there are many things I don't know.

---

### Post by Sarmacid on 2009-12-29
> **PDA1 said:**
> I don't know how to lock down a firewall and don't even know if I have one.

Ubuntu is new to me so there are many things I don't know.

Try```
sudo iptables -L
``` and put the output here.

---

### Post by PDA1 on 2009-12-29
Chain INPUT (policy DROP)
target     prot opt source               destination         
BLOCK_MATCH  all  --  anywhere             anywhere            mark match 0xffff 
INPUT_QUEUE  all  --  anywhere             anywhere            state NEW mark match !0xfffe 
ufw-before-logging-input  all  --  anywhere             anywhere            
ufw-before-input  all  --  anywhere             anywhere            
ufw-after-input  all  --  anywhere             anywhere            
ufw-after-logging-input  all  --  anywhere             anywhere            
ufw-reject-input  all  --  anywhere             anywhere            
ufw-track-input  all  --  anywhere             anywhere            

Chain FORWARD (policy DROP)
target     prot opt source               destination         
ufw-before-logging-forward  all  --  anywhere             anywhere            
ufw-before-forward  all  --  anywhere             anywhere            
ufw-after-forward  all  --  anywhere             anywhere            
ufw-after-logging-forward  all  --  anywhere             anywhere            
ufw-reject-forward  all  --  anywhere             anywhere            

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination         
BLOCK_MATCH  all  --  anywhere             anywhere            mark match 0xffff 
OUTPUT_QUEUE  all  --  anywhere             anywhere            state NEW mark match !0xfffe 
ufw-before-logging-output  all  --  anywhere             anywhere            
ufw-before-output  all  --  anywhere             anywhere            
ufw-after-output  all  --  anywhere             anywhere            
ufw-after-logging-output  all  --  anywhere             anywhere            
ufw-reject-output  all  --  anywhere             anywhere            
ufw-track-output  all  --  anywhere             anywhere            

Chain ALLOW_MATCH (16 references)
target     prot opt source               destination         
ACCEPT     all  --  anywhere             anywhere            

Chain BLOCK_MATCH (2 references)
target     prot opt source               destination         
REJECT     tcp  --  anywhere             anywhere            reject-with tcp-reset 
REJECT     all  --  anywhere             anywhere            reject-with icmp-port-unreachable 

Chain INPUT_QUEUE (1 references)
target     prot opt source               destination         
ALLOW_MATCH  all  --  anywhere             anywhere            source IP range 64.251.22.3-64.251.22.3 
ALLOW_MATCH  all  --  anywhere             anywhere            source IP range 74.125.93.109-74.125.93.109 
ALLOW_MATCH  all  --  anywhere             anywhere            source IP range 74.125.47.109-74.125.47.109 
ALLOW_MATCH  all  --  anywhere             anywhere            source IP range 224.0.0.251-224.0.0.251 
ALLOW_MATCH  all  --  anywhere             anywhere            source IP range 64.233.169.106-64.233.169.106 
ALLOW_MATCH  all  --  anywhere             anywhere            source IP range 74.125.45.109-74.125.45.109 
ALLOW_MATCH  all  --  anywhere             anywhere            source IP range 74.125.91.109-74.125.91.109 
ALLOW_MATCH  all  --  anywhere             anywhere            source IP range 63.245.209.91-63.245.209.91 
NFQUEUE    all  --  anywhere             anywhere            NFQUEUE num 253

Chain OUTPUT_QUEUE (1 references)
target     prot opt source               destination         
RETURN     tcp  --  anywhere             anywhere            tcp dpt:www 
RETURN     udp  --  anywhere             anywhere            udp dpt:domain 
ALLOW_MATCH  all  --  anywhere             anywhere            destination IP range 64.251.22.3-64.251.22.3 
ALLOW_MATCH  all  --  anywhere             anywhere            destination IP range 74.125.93.109-74.125.93.109 
ALLOW_MATCH  all  --  anywhere             anywhere            destination IP range 74.125.47.109-74.125.47.109 
ALLOW_MATCH  all  --  anywhere             anywhere            destination IP range 224.0.0.251-224.0.0.251 
ALLOW_MATCH  all  --  anywhere             anywhere            destination IP range 64.233.169.106-64.233.169.106 
ALLOW_MATCH  all  --  anywhere             anywhere            destination IP range 74.125.45.109-74.125.45.109 
ALLOW_MATCH  all  --  anywhere             anywhere            destination IP range 74.125.91.109-74.125.91.109 
ALLOW_MATCH  all  --  anywhere             anywhere            destination IP range 63.245.209.91-63.245.209.91 
NFQUEUE    all  --  anywhere             anywhere            NFQUEUE num 254

Chain ufw-after-forward (1 references)
target     prot opt source               destination         

Chain ufw-after-input (1 references)
target     prot opt source               destination         
RETURN     udp  --  anywhere             anywhere            udp dpt:netbios-ns 
RETURN     udp  --  anywhere             anywhere            udp dpt:netbios-dgm 
RETURN     tcp  --  anywhere             anywhere            tcp dpt:netbios-ssn 
RETURN     tcp  --  anywhere             anywhere            tcp dpt:microsoft-ds 
RETURN     udp  --  anywhere             anywhere            udp dpt:bootps 
RETURN     udp  --  anywhere             anywhere            udp dpt:bootpc 
RETURN     all  --  anywhere             anywhere            ADDRTYPE match dst-type BROADCAST 

Chain ufw-after-logging-forward (1 references)
target     prot opt source               destination         

Chain ufw-after-logging-input (1 references)
target     prot opt source               destination         

Chain ufw-after-logging-output (1 references)
target     prot opt source               destination         

Chain ufw-after-output (1 references)
target     prot opt source               destination         

Chain ufw-before-forward (1 references)
target     prot opt source               destination         
ufw-user-forward  all  --  anywhere             anywhere            

Chain ufw-before-input (1 references)
target     prot opt source               destination         
ACCEPT     all  --  anywhere             anywhere            
ACCEPT     all  --  anywhere             anywhere            state RELATED,ESTABLISHED 
ufw-logging-deny  all  --  anywhere             anywhere            state INVALID 
DROP       all  --  anywhere             anywhere            state INVALID 
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

Chain ufw-before-logging-forward (1 references)
target     prot opt source               destination         

Chain ufw-before-logging-input (1 references)
target     prot opt source               destination         

Chain ufw-before-logging-output (1 references)
target     prot opt source               destination         

Chain ufw-before-output (1 references)
target     prot opt source               destination         
ACCEPT     all  --  anywhere             anywhere            
ACCEPT     all  --  anywhere             anywhere            state RELATED,ESTABLISHED 
ufw-user-output  all  --  anywhere             anywhere            

Chain ufw-logging-allow (0 references)
target     prot opt source               destination         

Chain ufw-logging-deny (2 references)
target     prot opt source               destination         

Chain ufw-not-local (1 references)
target     prot opt source               destination         
RETURN     all  --  anywhere             anywhere            ADDRTYPE match dst-type LOCAL 
RETURN     all  --  anywhere             anywhere            ADDRTYPE match dst-type MULTICAST 
RETURN     all  --  anywhere             anywhere            ADDRTYPE match dst-type BROADCAST 
ufw-logging-deny  all  --  anywhere             anywhere            limit: avg 3/min burst 10 
DROP       all  --  anywhere             anywhere            

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
ACCEPT     tcp  --  anywhere             anywhere            state NEW 
ACCEPT     udp  --  anywhere             anywhere            state NEW 

Chain ufw-user-forward (1 references)
target     prot opt source               destination         

Chain ufw-user-input (1 references)
target     prot opt source               destination         

Chain ufw-user-limit (0 references)
target     prot opt source               destination         
LOG        all  --  anywhere             anywhere            limit: avg 3/min burst 5 LOG level warning prefix `[UFW LIMIT BLOCK] ' 
REJECT     all  --  anywhere             anywhere            reject-with icmp-port-unreachable 

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

---

### Post by Sarmacid on 2009-12-29
I just checked ufw and I think you should try ```
ufw disable
``` Before you try the other stuff I posted.

You actually have a firewall set up. I haven't used iptables in a while, but I think what you need to run is(as root)```
iptables -P INPUT ACCEPT
iptables -F
```This will take down all the rules and accept all incoming/outgoing packages so be careful.

---

### Post by PDA1 on 2009-12-29
Anybody have a comment to the previous post?

---

### Post by PDA1 on 2009-12-29
How do I get to "root"?

I'm new at this.

---

### Post by PDA1 on 2009-12-29
Your method of the UFW and then the IP stuff worked.

Now, how do I set my firewall so that I have some protection?

---

### Post by Sarmacid on 2009-12-30
[https://help.ubuntu.com/community/UFW](https://help.ubuntu.com/community/UFW)
[https://help.ubuntu.com/community/IptablesHowTo](https://help.ubuntu.com/community/IptablesHowTo)

Read those and you should be able to set up your own firewall with custom rules.

---

### Post by PDA1 on 2009-12-30
Man, that stuff really makes no sense to me at all.

Are there some default and basic settings I can set my firewall to so that it will block troublesome sites (or whatever it's supposed to block)?  Or, should I have my firewall enabled at all?

---

### Post by Sarmacid on 2009-12-30
I wouldn't worry with a firewall if I wasn't running any services or was behind a router. It's up to your paranoia level how much security you implement.

---

### Post by PDA1 on 2009-12-30
I assume that my wireless connection to my router constitutes the "router" requirement.

Is that correct?

Really what I don't want happening is someone getting access to my computer through the web and taking files from it.  Is that a likely situation?

---

### Post by Sarmacid on 2009-12-30
That's not very likely under your setup and if you don't have any services running. Have you installed any services on the ubuntu machine such as ssh, ftp or apache? If you haven't, there shouldn't be any problems.

---

### Post by PDA1 on 2009-12-30
I didn't setup any of the services you mentioned.  But, that doesn't mean my computer didn't do it all by itself, I suppose, under some sort of automatic modifications.

---

### Post by cariboo on 2009-12-30
The way to check if you have any servers running is to use System-->Administration-->Network Tools, and run a Port Scan. If you have a default installation the only port that should be open, is 631, which isn't a problem, because it only listens on 127.0.0.1. any other open ports mean that you have a server of some sort running.

---

### Post by adam814 on 2009-12-30
You might want to try gufw if you do end up running any of those servers in the future.  It gives you a graphical interface to edit your firewall rules.

Just do this"
```
sudo apt-get install gufw
```
Then go to System > Administration > Firewall Configuration

---

