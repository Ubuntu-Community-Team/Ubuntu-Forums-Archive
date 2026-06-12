---
title: "gufw doesnt seem to work..."
date: 2011-01-29
forum: Security
---

### Post by werty2010 on 2011-01-29
i installed gufw yesterday,enabled it ,set in/out-coming to deny and then opened transmission to see if it would download... and yes it did

maybe im wrong but shoudnt it block the traffic coming from transmission since i hadnt  added a rule yet?

could someone explain to me how this firewall works?

---

### Post by supererki on 2011-01-29
ufw is a front-end for iptables and by default iptables accepts all traffic. 

as admin : you can type 

iptables -L 

to see your current rules. So if you just enabled the firewall, it means that you have a firewall that accepts everything. 

Firstly : Configuring a firewall without the proper preparation is a very bad idea. Before you start configuring firewall you must be 100% sure what the firewall is supposed to do and what no. 
Having that said : Netfilter (which is behind iptables) have 3 building blocks: INPUT (incoming traffic) OUTPUT (traffic that comes from a process on a server) and FORWARD (traffic that comes to your network interface, but has to be routed). 
When a packet comes - there are 3 things you can do with this : ACCEPT, DROP or LOG. 

So first you should block all traffic 

iptables -P FORWARD DROP
iptables -P INPUT DROP
iptables -P OUTPUT DROP

And then you start making holes into it. Check man iptables or man ufw for further information. Also : take into consideration, that the rule will be effective from the very moment you press enter. Which means that if are doing it on some external machine - your connection will be automatically dropped.

---

### Post by Frogs Hair on 2011-01-29
If you set incoming  to reject , I would think it should do just that , but I haven't tested that setting yet . Here is a couple of links  on firewall basics and read the sticky in security forums.
   
[http://www.cs.wcupa.edu/~rkline/Ubuntu/firewall.html]("http://www.cs.wcupa.edu/%7Erkline/Ubuntu/firewall.html")

[https://help.ubuntu.com/community/UFW](https://help.ubuntu.com/community/UFW)

---

### Post by JKyleOKC on 2011-01-29
From "man ufw" in Terminal:```

On installation, ufw is disabled with a default incoming policy of deny and 
a default outgoing policy of allow, with stateful tracking for NEW connections.
```Thus a simple enabling should still have blocked incoming packets that were not in response to outgoing ones. That part about "stateful tracking for NEW connections" simply means that if you originated the connection, you can receive replies. Otherwise incoming packets don't get through.

I don't use P2P and routinely remove "transmission" from my systems immediately after installing them, but it's my understanding that the P2P protocols involve your machine offering the files to others at the same time you are downloading. That implies that it would originate packets, so that the "stateful tracking" that allows you to surf the web would also allow transmission's packets to come through...

You can add "deny" rules to UFW once it's enabled, to block the range of P2P ports.

---

### Post by supererki on 2011-01-29
> **Frogs Hair said:**
> If you set incoming  to reject , I would think it should do just that , but I haven't tested that setting yet . Here is a couple of links  on firewall basics and read the sticky in security forums.
   
[http://www.cs.wcupa.edu/~rkline/Ubuntu/firewall.html]("http://www.cs.wcupa.edu/%7Erkline/Ubuntu/firewall.html")

[https://help.ubuntu.com/community/UFW](https://help.ubuntu.com/community/UFW)

Difference between DROP and REJECT is that reject tells the source that firewall dropped the packed whereas drop quietly throws it away.

If you set all chains to DROP then your server is as secure as it can get (unless the you are in physical contact with the server:) )
It is so secure that even the graphical environment wont come up (loopback is down). 

So secondly you should enable lo 

iptables -A INPUT -i lo -j ACCEPT
iptables -A OUTPUT -o lo -j ACCEPT

and then add all other rules that you have in mind. 

So yes, if you set incoming to reject - thats exactly what gonna happen.

---

### Post by werty2010 on 2011-01-29
gufw is an interface for ufw,to make things simple,right? 
so if i set in/out-coming to "Deny" it should block internet traffic,yes?

[supererki]("http://ubuntuforums.org/member.php?u=741991") : i blocked all traffic with these commands: 
iptables -P FORWARD DROP
iptables -P INPUT DROP
iptables -P OUTPUT DROP

and still i could down/up-load...

maybe if i sent you an output from a command,would it make things easier to understand whats going on?

---

### Post by supererki on 2011-01-29
Firstly that is really weird. 
Do you have iptables running, try: 

service iptables status

If yes, post here :

lsmod | grep ip_tables
iptables -L

-----
But man - i wrote you, that touching iptables without knowing what you are doing is seriously bad idea. Do not blindly accept all commands provided in forums. 

If you really need to set up a firewall, I would suggest to follow this link :
[https://help.ubuntu.com/community/Gufw](https://help.ubuntu.com/community/Gufw)

---

### Post by werty2010 on 2011-01-29
> **supererki said:**
> Firstly that is really weird. 
Do you have iptables running, try: 

service iptables status

If yes, post here :

lsmod | grep ip_tables
iptables -L

-----
But man - i wrote you, that touching iptables without knowing what you are doing is seriously bad idea. Do not blindly accept all commands provided in forums. 

If you really need to set up a firewall, I would suggest to follow this link :
[https://help.ubuntu.com/community/Gufw](https://help.ubuntu.com/community/Gufw)

service iptables status  gives me:   iptables: unrecognized service

lsmod | grep ip_tables   gives me:
```
ip_tables              19139  3 iptable_nat,iptable_mangle,iptable_filter
x_tables               24423  14 ipt_MASQUERADE,xt_DSCP,ipt_REJECT,ipt_LOG,xt_limit,xt_tcpudp,xt_state,ipt_addrtype,iptable_nat,iptable_mangle,ip6table_filter,ip6_tables,iptable_filter,ip_tables

```iptables -L   gives me:
```
Chain INPUT (policy DROP)
target     prot opt source               destination         
ACCEPT     tcp  --  192.168.1.1          anywhere            tcp flags:!FIN,SYN,RST,ACK/SYN 
ACCEPT     udp  --  192.168.1.1          anywhere            
ACCEPT     all  --  anywhere             anywhere            
ACCEPT     icmp --  anywhere             anywhere            limit: avg 10/sec burst 5 
DROP       all  --  anywhere             255.255.255.255     
DROP       all  --  anywhere             192.168.1.255       
DROP       all  --  BASE-ADDRESS.MCAST.NET/8  anywhere            
DROP       all  --  anywhere             BASE-ADDRESS.MCAST.NET/8 
DROP       all  --  255.255.255.255      anywhere            
DROP       all  --  anywhere             0.0.0.0             
DROP       all  --  anywhere             anywhere            state INVALID 
LSI        all  -f  anywhere             anywhere            limit: avg 10/min burst 5 
INBOUND    all  --  anywhere             anywhere            
LOG_FILTER  all  --  anywhere             anywhere            
LOG        all  --  anywhere             anywhere            LOG level info prefix `Unknown Input' 
ufw-before-logging-input  all  --  anywhere             anywhere            
ufw-before-input  all  --  anywhere             anywhere            
ufw-after-input  all  --  anywhere             anywhere            
ufw-after-logging-input  all  --  anywhere             anywhere            
ufw-reject-input  all  --  anywhere             anywhere            
ufw-track-input  all  --  anywhere             anywhere            

Chain FORWARD (policy DROP)
target     prot opt source               destination         
ACCEPT     icmp --  anywhere             anywhere            limit: avg 10/sec burst 5 
LOG_FILTER  all  --  anywhere             anywhere            
LOG        all  --  anywhere             anywhere            LOG level info prefix `Unknown Forward' 
ufw-before-logging-forward  all  --  anywhere             anywhere            
ufw-before-forward  all  --  anywhere             anywhere            
ufw-after-forward  all  --  anywhere             anywhere            
ufw-after-logging-forward  all  --  anywhere             anywhere            
ufw-reject-forward  all  --  anywhere             anywhere            

Chain OUTPUT (policy DROP)
target     prot opt source               destination         
ACCEPT     tcp  --  lalalandeee-Inspiron-N5010  192.168.1.1         tcp dpt:domain 
ACCEPT     udp  --  lalalandeee-Inspiron-N5010  192.168.1.1         udp dpt:domain 
ACCEPT     all  --  anywhere             anywhere            
DROP       all  --  BASE-ADDRESS.MCAST.NET/8  anywhere            
DROP       all  --  anywhere             BASE-ADDRESS.MCAST.NET/8 
DROP       all  --  255.255.255.255      anywhere            
DROP       all  --  anywhere             0.0.0.0             
DROP       all  --  anywhere             anywhere            state INVALID 
OUTBOUND   all  --  anywhere             anywhere            
LOG_FILTER  all  --  anywhere             anywhere            
LOG        all  --  anywhere             anywhere            LOG level info prefix `Unknown Output' 
ufw-before-logging-output  all  --  anywhere             anywhere            
ufw-before-output  all  --  anywhere             anywhere            
ufw-after-output  all  --  anywhere             anywhere            
ufw-after-logging-output  all  --  anywhere             anywhere            
ufw-reject-output  all  --  anywhere             anywhere            
ufw-track-output  all  --  anywhere             anywhere            

Chain INBOUND (1 references)
target     prot opt source               destination         
ACCEPT     tcp  --  anywhere             anywhere            state RELATED,ESTABLISHED 
ACCEPT     udp  --  anywhere             anywhere            state RELATED,ESTABLISHED 
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

Chain OUTBOUND (1 references)
target     prot opt source               destination         
ACCEPT     icmp --  anywhere             anywhere            
ACCEPT     tcp  --  anywhere             anywhere            state RELATED,ESTABLISHED 
ACCEPT     udp  --  anywhere             anywhere            state RELATED,ESTABLISHED 
ACCEPT     all  --  anywhere             anywhere            

Chain ufw-after-forward (1 references)
target     prot opt source               destination         

Chain ufw-after-input (1 references)
target     prot opt source               destination         
ufw-skip-to-policy-input  udp  --  anywhere             anywhere            udp dpt:netbios-ns 
ufw-skip-to-policy-input  udp  --  anywhere             anywhere            udp dpt:netbios-dgm 
ufw-skip-to-policy-input  tcp  --  anywhere             anywhere            tcp dpt:netbios-ssn 
ufw-skip-to-policy-input  tcp  --  anywhere             anywhere            tcp dpt:microsoft-ds 
ufw-skip-to-policy-input  udp  --  anywhere             anywhere            udp dpt:bootps 
ufw-skip-to-policy-input  udp  --  anywhere             anywhere            udp dpt:bootpc 
ufw-skip-to-policy-input  all  --  anywhere             anywhere            ADDRTYPE match dst-type BROADCAST 

Chain ufw-after-logging-forward (1 references)
target     prot opt source               destination         
LOG        all  --  anywhere             anywhere            limit: avg 3/min burst 10 LOG level warning prefix `[UFW BLOCK] ' 

Chain ufw-after-logging-input (1 references)
target     prot opt source               destination         
LOG        all  --  anywhere             anywhere            limit: avg 3/min burst 10 LOG level warning prefix `[UFW BLOCK] ' 

Chain ufw-after-logging-output (1 references)
target     prot opt source               destination         
LOG        all  --  anywhere             anywhere            limit: avg 3/min burst 10 LOG level warning prefix `[UFW BLOCK] ' 

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
LOG        all  --  anywhere             anywhere            limit: avg 3/min burst 10 LOG level warning prefix `[UFW ALLOW] ' 

Chain ufw-logging-deny (2 references)
target     prot opt source               destination         
RETURN     all  --  anywhere             anywhere            state INVALID limit: avg 3/min burst 10 
LOG        all  --  anywhere             anywhere            limit: avg 3/min burst 10 LOG level warning prefix `[UFW BLOCK] ' 

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

Chain ufw-skip-to-policy-forward (0 references)
target     prot opt source               destination         
DROP       all  --  anywhere             anywhere            

Chain ufw-skip-to-policy-input (7 references)
target     prot opt source               destination         
DROP       all  --  anywhere             anywhere            

Chain ufw-skip-to-policy-output (0 references)
target     prot opt source               destination         
DROP       all  --  anywhere             anywhere            

Chain ufw-track-input (1 references)
target     prot opt source               destination         

Chain ufw-track-output (1 references)
target     prot opt source               destination         

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
```i try not to blindly follow everyones advise but i really want to understand whats happening

---

### Post by JKyleOKC on 2011-01-29
Those lines that show "ACCEPT all anywhere anywhere" effectively open the firewall for everything and make all the rest of the rules meaningless!

It looks as if you may have tried several different firewall building programs, that created all those additional filtering rules. The basic iptables firewalls require only three chains: INPUT, OUTPUT, and FORWARD. If each of these has its policy set to DROP, and no other rules in any of them, your machine should be totally isolated from all outside connections (including even itself as localhost). The default settings for UFW provide a good starting point.

At this stage I would flush all of the existing rules, and start over by enabling UFW. From there I would study its "man" page (which will tell you much more than you probably want to know for now, but which has a number of good examples near the bottom of the file), and ask here about anything that doesn't seem to make sense.

The various firewall builder programs available all do things differently so a mix and match from several of them can result in an ineffective mishmash of rules. So can taking everyone's advice, obviously.

The iptables/netfilter capability in the kernel has many many options, most of which aren't needed or useful for the usual home installation. That's why my motto for it is "simplest is best."

EDIT: Note that the rules are applied in the order that they show up in the listing, so that nothing in your INPUT chain after its third rule will ever be reached. Sequence is extremely important in this file!

I've found the "iptables-save" and "iptables-restore" commands to be most useful, also, since I can save my working rules set and restore it simply when re-booting, with no need to run any other builder program.

---

### Post by supererki on 2011-01-29
huh. 
It seems that you accept all packets coming from everywhere
ACCEPT     all  --  anywhere             anywhere  

I have to agree with JKyleOKC, you should start from a scratch. 

But first you should think what exactly you want the firewall to do. Write down everything you want to allow. 
Assuming that you have 1 NIC, you could create a matrix like this :

SERVICE NEEDED                        INBOUND/OUTBOUND

DNS                                    in + out
SSH                                    in + out
HTTP                                   in
TORRENT                                in + out
SMTP                                   in + out

etc

So when you start from scrath - you have 3 CHAINS that by default are empty. Next you have to add rules to chains, where you define packet type and default action. The rules are evaluated from top to bottom. As soon as a rule matches a packet, the rule will say that "ok, this is my packet" and all other rules below that will not be applied (except LOG). 
And then - after rules you must define a policy which you should set to DROP (means that only packets that you allow will get thru, everything else will be dropped). And thats pretty much it. All you have to do is to store the rules to some place where they will be loaded after next boot. 

-------------
So firstly you set the default policys :

iptables -P FORWARD DROP
iptables -P INPUT DROP
iptables -P OUTPUT DROP

This means that we do not allow absolutely anything. nothing. zero. nada. 
Then you should define the rules themselves. Basically its like this :

iptables <position> <chain> <matching> <target>

Position. Here you specify following options :

1. -A   - add (to the end of chain)
2. -D   - delete rule
3. -I   - insert (to specific position)
4. -R   - replace (does that:))

Chain is INPUT / OUTPUT / FORWARD

The matching part is important. In there you can set following :

1. Interface     - in/out
2. IP            - source (-s) and destination (-d) IPs
3. Protocol
4. Port          - source port (--sport) and destination port (--dport)

Note that you don't have to use them all at the same time. so '-p TCP --dport 25' would apply to all IP-s. 

Target - is the action that will occur when packet matches the rule : ACCEPT / REJECT / DROP / LOG

---------------
One more thing you should look into is the 'state'. You can use the '-m state --state <state>' to apply the rules for packets only in specific state. For example, following line  

iptables -A INPUT -m state --state ESTABLISHED,RELATED -j ACCEPT

means :
that all packets that are part of an already established or related session are allowed in.
---------------

Based on that information you should be able to configure the firewall.

---

### Post by uRock on 2011-01-29
Werty2010, have you tried any other firewall applications? If yes, then please list them so that we can help purge their settings and get you system to the secure state you are wanting.



Thread moved to the Security Discussions sub-forum.

---

