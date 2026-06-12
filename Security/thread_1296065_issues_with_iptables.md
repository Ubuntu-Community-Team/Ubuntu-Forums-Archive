---
title: "issues with iptables"
date: 2009-10-20
forum: Security
---

### Post by jsvidyad on 2009-10-20
Hi All!!!

	I'm running the 64 bit version of ubuntu 9.04. I am also using firestarter as a gui for iptables. I have set up firestarter so that all incoming connections are dropped, all outgoing connections are allowed and all ICMP packets are dropped. But, when I checked the output of sudo /sbin/iptables -L , it looked like all incoming connections are accepted from the ip addresses 218.248.255.139 and 218.248.255.212 . Now, I know very little about iptables and I'm not sure if my interpretation is correct. I will attach the output of sudo /sbin/iptables -L here and can you have a look at it?? Please let me know if I'm correct and if I'm correct, why these two ip addresses are allowed complete incoming access.


Chain INPUT (policy DROP) 
target     prot opt source               destination         
ACCEPT     tcp  --  218.248.255.139      anywhere            tcp flags:!FIN,SYN,RST,ACK/SYN 
ACCEPT     udp  --  218.248.255.139      anywhere            
ACCEPT     tcp  --  218.248.255.212      anywhere            tcp flags:!FIN,SYN,RST,ACK/SYN 
ACCEPT     udp  --  218.248.255.212      anywhere            
ACCEPT     all  --  anywhere             anywhere            
LSI        udp  --  anywhere             anywhere            udp dpt:33434 
LSI        icmp --  anywhere             anywhere            
DROP       all  --  anywhere             255.255.255.255     
DROP       all  --  224.0.0.0/8          anywhere            
DROP       all  --  anywhere             BASE-ADDRESS.MCAST.NET/8 
DROP       all  --  255.255.255.255      anywhere            
DROP       all  --  anywhere             0.0.0.0             
DROP       all  --  anywhere             anywhere            state INVALID 
LSI        all  -f  anywhere             anywhere            limit: avg 10/min burst 5 
INBOUND    all  --  anywhere             anywhere            
LOG_FILTER  all  --  anywhere             anywhere            
LOG        all  --  anywhere             anywhere            LOG level info prefix `Unknown Input' 

Chain FORWARD (policy DROP) 
target     prot opt source               destination         
LSI        udp  --  anywhere             anywhere            udp dpt:33434 
LSI        icmp --  anywhere             anywhere            
LOG_FILTER  all  --  anywhere             anywhere            
LOG        all  --  anywhere             anywhere            LOG level info prefix `Unknown Forward' 

Chain OUTPUT (policy DROP) 
target     prot opt source               destination         
ACCEPT     tcp  --  117.199.0.236        218.248.255.139     tcp dpt:domain 
ACCEPT     udp  --  117.199.0.236        218.248.255.139     udp dpt:domain 
ACCEPT     tcp  --  117.199.0.236        218.248.255.212     tcp dpt:domain 
ACCEPT     udp  --  117.199.0.236        218.248.255.212     udp dpt:domain 
ACCEPT     all  --  anywhere             anywhere            
DROP       all  --  224.0.0.0/8          anywhere            
DROP       all  --  anywhere             224.0.0.0/8         
DROP       all  --  255.255.255.255      anywhere            
DROP       all  --  anywhere             0.0.0.0             
DROP       all  --  anywhere             anywhere            state INVALID 
OUTBOUND   all  --  anywhere             anywhere            
LOG_FILTER  all  --  anywhere             anywhere            
LOG        all  --  anywhere             anywhere            LOG level info prefix `Unknown Output' 

Chain INBOUND (1 references) 
target     prot opt source               destination         
ACCEPT     tcp  --  anywhere             anywhere            state RELATED,ESTABLISHED 
ACCEPT     udp  --  anywhere             anywhere            state RELATED,ESTABLISHED 
LSI        all  --  anywhere             anywhere            

Chain LOG_FILTER (5 references) 
target     prot opt source               destination         

Chain LSI (6 references) 
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

---

### Post by Lars Noodén on 2009-10-20
Follow it, step by step as an imaginary packet drops through the chains.

You should at least allow some ICMP, because without it your network is broken.  

Can you describe your goal first?  It would be easier to help you assess whether your IP Tables rules help you toward that goal if it is known. 

You can also test from another machine using zenmap / nmap or even OpenVAS.

---

### Post by jsvidyad on 2009-10-21
I don't want to allow any incoming connections from any ip address whatsoever. Does the above IPTable help with that??

---

### Post by Lars Noodén on 2009-10-21
And is that machine intended to be a router, switch or gateway?  Or is it a server or desktop?

---

### Post by QLee on 2009-10-21
> **jsvidyad said:**
> I don't want to allow any incoming connections from any ip address whatsoever. Does the above IPTable help with that??

Be careful what you ask for, someone may help you do this and then you would not be able to surf the 'Net or post to this forum (if you query, there has to be somewhere for the answer to come back). The easiest way to accomplish what you state is unplug. Chances are good that you only don't want unrequested connections.

Perhaps rephrase your goal, poster Lars' question is a good way to start.

---

### Post by Lars Noodén on 2009-10-21
> **jsvidyad said:**
> I don't want to allow any incoming connections from any ip address whatsoever. Does the above IPTable help with that??

Yes.  IPTables can do that.  However, as QLee implied that may not be what you actually want to do. ;)  Before testing any experiments with IP Tables you want to leave a way back in.

```

sudo iptables-save > /tmp/iptables.current.situation
sudo sh -c "echo 'iptables-restore < /tmp/iptables.current.situation' | at now +10 minutes"

```

For the machine to be any use at all, you have to let some things in.  Which things depends on the usage and setup of the machine:
Are you setting up IPTables for a server or workstation, or for a router or switch, or something else?  One network interface, two, three, more?  Knowing these allows you to get what you need.

---

### Post by The Cog on 2009-10-21
You should always use **sudo iptables -vL** in order to also see any port restrictions, such as allow anything from interface lo which otherwise looks like allow anything at all.

These rules were generated by some kind of automated rule generator - a configuration GUI perhaps. It might be instructive to look at that. Are those addresses on your local machine?

---

### Post by rampageoberon on 2009-10-22
> **jsvidyad said:**
> I don't want to allow any incoming connections from any ip address whatsoever. Does the above IPTable help with that??

Hi there,

iptables the linux firewall is installed by default. It does allow incoming connections when an application you run wants to listen on a particular port. (by default policy is to accept, if you set policy to drop then it will drop all packets until explicitly told to accept)

As long as there is no server application running, in the default setup no incoming connections will succeed and the corresponding ports are naturally blocked.

For example skype will attempt to listen on a particular port for incoming connections (and it is beneficial to allow this in order to get a better connection)

I prefer writing the script for iptables manually, though my experience is limited, rather than using a gui to do the configuration. In that way you can learn exactly what the script is doing and it can be more precise.

Something like the below code will drop all incoming packets. But I'd be careful doing this. In my experience the default config on ubuntu firewall is fairly secure, however it is good to tweak it to your liking.
```
sudo iptables -I INPUT -j DROP
```

Hope this helps

---

### Post by bodhi.zazen on 2009-10-22
> **rampageoberon said:**
> Hi there,

iptables by default has all incoming connections blocked. It however does allow incoming connections when an application you run wants to listen on a particular port. 

I am sorry, but that is not true. by default iptables is installed, but it is not configured, and thus allow all traffic.

On a fresh install, do

```
sudo iptables -L -v
```

> (by default policy is to accept, if you set policy to drop then it will drop all packets until explicitly told to accept)

As long as there is no server application running, in the default setup no incoming connections will succeed and the corresponding ports are naturally blocked.

For example skype will attempt to listen on a particular port for incoming connections (and it is beneficial to allow this in order to get a better connection)

I prefer writing the script for iptables manually, though my experience is limited, rather than using a gui to do the configuration. In that way you can learn exactly what the script is doing and it can be more precise.

Something like the below code will drop all incoming packets. But I'd be careful doing this. In my experience the default config on ubuntu firewall is fairly secure, however it is good to tweak it to your liking.
```
sudo iptables -I INPUT -j DROP
```Hope this helps

See [http://bodhizazen.net/Tutorials/iptables/](http://bodhizazen.net/Tutorials/iptables/)

---

### Post by jsvidyad on 2009-10-23
Can someone please look at the iptables rules given at the top of this thread and tell me if iptables is setup to drop all incoming connections?? As of now, it seems to me as if it is set to accept all incoming connections from two ip addresses. This is my only concern.

---

### Post by jsvidyad on 2009-10-23
Actually i just want to drop all unrequested connections. sorry I wasn't clear earlier

---

### Post by bodhi.zazen on 2009-10-23
> **jsvidyad said:**
> Actually i just want to drop all unrequested connections. sorry I wasn't clear earlier

To be honest, it appears your rules are a bit of a mess, but it is hard to know.

In general my advice is :

1. List your rules with :

```
sudo iptables -L -v
```

This gives you more details.

2. Keep in mind, the order of your rules counts ...

so if you look at this block :

> DROP       all  --  anywhere             0.0.0.0             
DROP       all  --  anywhere             anywhere            state INVALID 
LSI        all  -f  anywhere             anywhere            limit: avg 10/min burst 5 

the first rule is hit, DROP all 

and so the other rules are not processed. 

Now it depends on the details of the rules, which only iptalbes -L -v will show us ...

3. It is complex enough you should not rely on yourself or anyone else to look over the rules ...

YOU NEED TO TEST THE RULES yourself.

This means ...

port scanning yourself with nmap or a similar tool, ideally IMO, form another machine on your LAN.

---

