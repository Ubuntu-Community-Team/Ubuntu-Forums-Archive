---
title: "iptables"
date: 2010-02-19
forum: Security
---

### Post by adeelm on 2010-02-19
hi everyone

               I am trying to configure iptables and allow only specific traffic to enter and leave my ubuntu computer but I am having some problems with it. the iptables that I configured are...

:INPUT ACCEPT [33:3703]
:FORWARD ACCEPT [0:0]
:OUTPUT ACCEPT [42:3336]
-A INPUT -s 10.0.0.0/8 -i eth0 -j ACCEPT 
-A INPUT -p tcp -m tcp --dport 22 -j ACCEPT 
-A INPUT -p tcp -m tcp --dport 80 -j ACCEPT 
-A INPUT -i eth0 -p tcp -m tcp --sport 1024:65535 --dport 80 -m state --state NEW -j ACCEPT 
[COLOR=Red]_**[SIZE=3]-A INPUT -j DROP[/SIZE]**_[/COLOR]
-A OUTPUT -d 10.0.0.0/8 -o eth0 -j ACCEPT 
-A OUTPUT -p tcp -m tcp --dport 22 -j ACCEPT 
-A OUTPUT -p tcp -m tcp --dport 80 -j ACCEPT 
-A OUTPUT -o eht0 -m state --state RELATED,ESTABLISHED -j ACCEPT 
[COLOR=Red]_**[SIZE=3]-A OUTPUT -j DROP[/SIZE]**_[/COLOR]


When the lines in RED color are entered all the incomming and outgoing traffic are blocked.

What I want is that all my http, https, ssh and my lan traffic are allowed. every other traffic (incomming/outgoing) should be blocked.

Please provide a solution to this issue.

Thanks

Adeel.

---

### Post by gombadi on 2010-02-19
Just before the main drop rules that you highlighted in red, insert a log rule so you can see what packets it is dropping. That will give you a clue to what rules need to be added or changed.

---

### Post by bodhi.zazen on 2010-02-19
What traffic is blocked exactly ?

https is port 443.
and you should probably accept traffic on your lo interface.

Zero iptables ```
iptables -Z
```

try to connect or generate outgoing traffic

post the output of ```
iptables -L -v
```

---

### Post by cdenley on 2010-02-19
I believe that will filter traffic coming from other servers, since established traffic isn't allowed in your INPUT chain and the destination port will be a high, random number for the client end. You wouldn't be able to browse the web or anything.

I think the last INPUT rule is redundant, since you already accept all traffic on port 80. Replace that with a rule accepting established connections.

---

### Post by The Cog on 2010-02-19
There's a typo on the output list, interface eht0 should be eth0.

cdenley is right about your missing established rule inbound.

This rule is redundant because the prior rule allows all that and more anyway, on top of which I don't see why you should care about your client's source port:
> -A INPUT -i eth0 -p tcp -m tcp --sport 1024:65535 --dport 80 -m state --state NEW -j ACCEPT

You are not allowing DNS queries out (UdP port 53) so you won't be able to connect to anything by name. Also, without cdenley's established input rule, the DNS replies wouldn't be allowed back in anyway.

You should allow the loopback port to talk to itself or strange things like print spooling will break:
> iptables -A INPUT -i lo -j ACCEPT

---

### Post by adeelm on 2010-02-21
Thanks all,

apologize for the late reply but I am looking in to what you have said. I will tell you after I update the iptables and see if it works.

Thanks a lot.

Adeel

---

### Post by adeelm on 2010-02-21
hi bodhi.zazen,

I have a little change. that is i have removed this from ptables as The Cog suggested. 
-A INPUT -i eth0 -p tcp -m tcp --sport 1024:65535 --dport 80 -m state --state NEW -j ACCEPT 			 		

You asked for the output of iptables -L -v. here it is.

root@Infosec-Lab04:~/iptables# iptables -L -v
Chain INPUT (policy ACCEPT 2081 packets, 1667K bytes)
 pkts bytes target     prot opt in     out     source               destination         
   19  2525 ACCEPT     all  --  eth0   any     10.0.0.0/8           anywhere            
    0     0 ACCEPT     tcp  --  any    any     anywhere             anywhere            tcp dpt:ssh 
    0     0 ACCEPT     tcp  --  any    any     anywhere             anywhere            tcp dpt:www 

Chain FORWARD (policy ACCEPT 0 packets, 0 bytes)
 pkts bytes target     prot opt in     out     source               destination         

Chain OUTPUT (policy ACCEPT 1943 packets, 352K bytes)
 pkts bytes target     prot opt in     out     source               destination         
   15  2341 ACCEPT     all  --  any    eth0    anywhere             10.0.0.0/8          
    0     0 ACCEPT     tcp  --  any    any     anywhere             anywhere            tcp dpt:ssh 
  246 34395 ACCEPT     tcp  --  any    any     anywhere             anywhere            tcp dpt:www 
    0     0 ACCEPT     all  --  any    eht0    anywhere             anywhere            state RELATED,ESTABLISHED 


Thanks

Adeel.

---

### Post by adeelm on 2010-02-21
> **bodhi.zazen said:**
> What traffic is blocked exactly ?

https is port 443.
and you should probably accept traffic on your lo interface.

Zero iptables ```
iptables -Z
```try to connect or generate outgoing traffic

post the output of ```
iptables -L -v
```


I am being hit by traffic from my local lan. that is I am getting queries from multiple windows based machines. I have checked it with Wireshark. I am getting all king of queries.

Thanks

Adeel

---

### Post by The Cog on 2010-02-24
I'm not sure you actually need a firewall. What services are you running? The output of ```
netstat -lntu
``` will tell us. If it's only HTTP and SSH then you are already allowing those in so the firewall isn't doing anything useful inbound. On the other hand, you do have a rule that blocks any other services to addresses outside of network 10, so if you do have other services running then the firewall rules do have something useful to do.

In terms of your outbound filter, I have never really worried about blocking outbound connections - if your PC is making naughty outbound connections then you are already compromised and the naughty app is likely to either disable the firewall or use port 80 anyway. So I don't personally see blocking outgoing calls as a good reason (on its own) for having a firewall. 

Your inbound and outbound policies are both Permit, so at the moment iptables isn't blocking anything. I guess this is because of the difficulties you were having when you start blocking things.

You still haven't allowed UDP port 53 out, so DNS wouldn't work because the queries couldn't get out. And without the RELATED,ESTABLISHED inbound, the reply couldn't get through either. Unless your DNS server is on network 10, that is).

You still haven't allowed interface lo to talk to itself, so some things like print spooling wouldn't work.

You should remember that wireshark sees the packets on the interface - before iptables drops inbound packets and after iptables filters them outbound. So you will see inbound packets even if iptables is going to drop them, and won't see any outbound packets that iptables decides to drop.

You still have the "eht0" typo in the OUTPUT rules.

Do the queries from the windows PCs worry you? If so, what type of query are they? If they're to services that aren't running then they are doing no harm and you are probably better off forgetting about them than spending a lot of time struggling with iptables.

---

### Post by adeelm on 2010-02-28
> **The Cog said:**
> I'm not sure you actually need a firewall. What services are you running? The output of ```
netstat -lntu
``` will tell us. If it's only HTTP and SSH then you are already allowing those in so the firewall isn't doing anything useful inbound. On the other hand, you do have a rule that blocks any other services to addresses outside of network 10, so if you do have other services running then the firewall rules do have something useful to do.

In terms of your outbound filter, I have never really worried about blocking outbound connections - if your PC is making naughty outbound connections then you are already compromised and the naughty app is likely to either disable the firewall or use port 80 anyway. So I don't personally see blocking outgoing calls as a good reason (on its own) for having a firewall. 

Your inbound and outbound policies are both Permit, so at the moment iptables isn't blocking anything. I guess this is because of the difficulties you were having when you start blocking things.

You still haven't allowed UDP port 53 out, so DNS wouldn't work because the queries couldn't get out. And without the RELATED,ESTABLISHED inbound, the reply couldn't get through either. Unless your DNS server is on network 10, that is).

You still haven't allowed interface lo to talk to itself, so some things like print spooling wouldn't work.

You should remember that wireshark sees the packets on the interface - before iptables drops inbound packets and after iptables filters them outbound. So you will see inbound packets even if iptables is going to drop them, and won't see any outbound packets that iptables decides to drop.

You still have the "eht0" typo in the OUTPUT rules.

Do the queries from the windows PCs worry you? If so, what type of query are they? If they're to services that aren't running then they are doing no harm and you are probably better off forgetting about them than spending a lot of time struggling with iptables.

Hi,

Sorry every one. I was buzy with a project so I could not reply.

The output of netstat -lntu.

tcp        0      0 0.0.0.0:1344            0.0.0.0:*               LISTEN     
tcp        0      0 0.0.0.0:5800            0.0.0.0:*               LISTEN     
tcp        0      0 0.0.0.0:139             0.0.0.0:*               LISTEN     
tcp        0      0 0.0.0.0:5900            0.0.0.0:*               LISTEN     
tcp        0      0 0.0.0.0:10000           0.0.0.0:*               LISTEN     
tcp        0      0 0.0.0.0:80              0.0.0.0:*               LISTEN     
tcp        0      0 127.0.0.1:631           0.0.0.0:*               LISTEN     
tcp        0      0 0.0.0.0:3128            0.0.0.0:*               LISTEN     
tcp        0      0 0.0.0.0:25              0.0.0.0:*               LISTEN     
tcp        0      0 0.0.0.0:445             0.0.0.0:*               LISTEN     
tcp6       0      0 :::5901                 :::*                    LISTEN     
tcp6       0      0 ::1:631                 :::*                    LISTEN     
udp        0      0 127.0.0.1:161           0.0.0.0:*                          
udp        0      0 0.0.0.0:44194           0.0.0.0:*                          
udp        0      0 0.0.0.0:34862           0.0.0.0:*                          
udp        0      0 0.0.0.0:3130            0.0.0.0:*                          
udp        0      0 0.0.0.0:54089           0.0.0.0:*                          
udp        0      0 0.0.0.0:5353            0.0.0.0:*                          
udp        0      0 172.16.78.1:137         0.0.0.0:*                          
udp        0      0 192.168.7.1:137         0.0.0.0:*                          
udp        0      0 10.0.0.4:137            0.0.0.0:*                          
udp        0      0 0.0.0.0:137             0.0.0.0:*                          
udp        0      0 172.16.78.1:138         0.0.0.0:*                          
udp        0      0 192.168.7.1:138         0.0.0.0:*                          
udp        0      0 10.0.0.4:138            0.0.0.0:*                          
udp        0      0 0.0.0.0:138             0.0.0.0:*                          
udp        0      0 0.0.0.0:10000           0.0.0.0:*    


I was getting messeges from windows I do not remember now. They were broadcasts. and my network traffic was going up to 400 Kbps. I have tested the faulty windows machine and found out that it was a cisco VPN software that was generating all that traffic. I uninstalled it and now the broadcasts have finished.

Thanks all of you for your help.

Adeel

---

