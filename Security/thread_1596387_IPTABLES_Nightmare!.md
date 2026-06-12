---
title: "IPTABLES Nightmare!"
date: 2010-10-14
forum: Security
---

### Post by horizonuser on 2010-10-14
I have been trying to find the answer to this everywhere I can think of but I can't!

I have iptabels configured in a very simple manner (see below). I need to restrict all incoming traffic to just tcp:22 and then only allow 3 source IP address access everything on the system. I then deny all. The trouble is that while this all works the last line below stops all traffic from leaving/returning from the local server itself - it is like the it is ignoring the "Esablished connections" entry. This result is that all the rules work except now the server can't do anything itself (DNS, HTTP, FTP etc)

Can anyone help?

1      141 16016 ACCEPT     all  --  lo     *       0.0.0.0/0            0.0.0.0/0
2      820 67372 ACCEPT     all  --  *      *       86.x.y.z	         0.0.0.0/0
3        0     0 ACCEPT     all  --  *      *       0.0.0.0/0            0.0.0.0/0           ctstate RELATED,ESTABLISHED
4        0     0 ACCEPT     all  --  *      *       0.0.0.0/0            0.0.0.0/0           state RELATED,ESTABLISHED
5      494 38012 ACCEPT     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           tcp dpt:22
6        0     0 ACCEPT     all  --  *      *       83.xx.yy.zz          0.0.0.0/0
7        0     0 ACCEPT     all  --  *      *       82.xx.yy.zz	         0.0.0.0/0
8        0     0 ACCEPT     tcp  --  *      *       137.xx.yy.zz         0.0.0.0/0           tcp dpt:80
9        0     0 ACCEPT     tcp  --  *      *       137.xx.yy.zz         0.0.0.0/0           tcp dpt:8080
10      15  1444 DROP       all  --  *      *       0.0.0.0/0            0.0.0.0/0


EDIT: Was originally this: note the scrollbars (scroll right to see ESTABLISHED rule)

```


1      141 16016 ACCEPT     all  --  lo     *       0.0.0.0/0            0.0.0.0/0
2      820 67372 ACCEPT     all  --  *      *       86.x.y.z	         0.0.0.0/0
3        0     0 ACCEPT     all  --  *      *       0.0.0.0/0            0.0.0.0/0           ctstate RELATED,ESTABLISHED
4        0     0 ACCEPT     all  --  *      *       0.0.0.0/0            0.0.0.0/0           state RELATED,ESTABLISHED
5      494 38012 ACCEPT     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           tcp dpt:22
6        0     0 ACCEPT     all  --  *      *       83.xx.yy.zz          0.0.0.0/0
7        0     0 ACCEPT     all  --  *      *       82.xx.yy.zz	         0.0.0.0/0
8        0     0 ACCEPT     tcp  --  *      *       137.xx.yy.zz         0.0.0.0/0           tcp dpt:80
9        0     0 ACCEPT     tcp  --  *      *       137.xx.yy.zz         0.0.0.0/0           tcp dpt:8080
10      15  1444 DROP       all  --  *      *       0.0.0.0/0            0.0.0.0/0
```

---

### Post by BkkBonanza on 2010-10-14
Can you post your rules? The listing above does not provide enough info. I assume that's your INPUT chain but what about your OUTPUT chain? That is the one that would affect the server trying to do things that you say it can't.

---

### Post by The Cog on 2010-10-14
To be really sure we get everything, posting the output of **sudo iptables -nvL** would be good.

---

### Post by horizonuser on 2010-10-15
> **The Cog said:**
> To be really sure we get everything, posting the output of **sudo iptables -nvL** would be good.

Hi Cog,
        That output above is the results of iptables -L -vn.
What were you expecting to see? I did leave out the other chains, which are below.

Chain FORWARD (policy ACCEPT 0 packets, 0 bytes)
 pkts bytes target     prot opt in     out     source               destination                                                                        

Chain OUTPUT (policy ACCEPT 842K packets, 497M bytes)
 pkts bytes target     prot opt in     out     source               destination

---

### Post by SeijiSensei on 2010-10-15
> The trouble is that while this all works the last line below stops all traffic from leaving/returning from the local server itself - it is like the it is ignoring the "Esablished connections" entry

I don't see any "established connections" rule, so you're not allowing reply packets.  Add a line like this at the top of the ruleset:

```
iptables -A INPUT -m state --state ESTABLISHED,RELATED -j ACCEPT
```

---

### Post by horizonuser on 2010-10-15
SeijiSensei: look at my first post, the ESTABLISHED rule is there.

---

### Post by The Cog on 2010-10-15
> **horizonuser said:**
> SeijiSensei: look at my first post, the ESTABLISHED rule is there.

I'm looking, and I don't see it. And I really don't feel like fighting with people who don't want to tell you the full story - I like helping people, not playing hide-and-seek guessing games with them.

Sorry if that offends - I guess I'm just feeling tired and grumpy. But really, supporting someone who filters the information you ask for is a hundred times harder than supporting someone who supplies all the information.

---

### Post by SeijiSensei on 2010-10-16
> **The Cog said:**
> I'm looking, and I don't see it.

Me, neither.  Thought perhaps I was going blind.

---

### Post by HermanAB on 2010-10-16
Howdy,

You can fight iptables yourself, or you can install UFW.

---

### Post by horizonuser on 2010-10-16
> **The Cog said:**
> I'm looking, and I don't see it. And I really don't feel like fighting with people who don't want to tell you the full story - I like helping people, not playing hide-and-seek guessing games with them.

Sorry if that offends - I guess I'm just feeling tired and grumpy. But really, supporting someone who filters the information you ask for is a hundred times harder than supporting someone who supplies all the information.

Hi - I do appreiciate your help and I am not purposefully hiding anything! The ESTABLISHED rule is there in the first output I posted at the top of the post, but here it is again (copy and pasted from my first post - rule number 3 and 4 although I should only need one of these rule). Please let me know what else I need so you might advise further. I posted the other 2 chains in a later post. 

(My first post shows my INPUT chain but I need to scroll over the scroll bars to see the ESTABLISHED rule, can you not see this?

3        0     0 ACCEPT     all  --  *      *       0.0.0.0/0            0.0.0.0/0           ctstate RELATED,ESTABLISHED
4        0     0 ACCEPT     all  --  *      *       0.0.0.0/0            0.0.0.0/0           state RELATED,ESTABLISHED

EDIT: I removed the CODE tags from my first post which seemed to be causing a scroll bar on the output, you should be able to see the ESTABLISHED rules now. 
EDIT 2: Repost of complete "iptables -L -vn":

 iptables -L -vn
Chain INPUT (policy ACCEPT 707K packets, 73M bytes)
 pkts bytes target     prot opt in     out     source               destination
66641 8300K ACCEPT     all  --  lo     *       0.0.0.0/0            0.0.0.0/0
 1784  143K ACCEPT     all  --  *      *       86.x.x.x             0.0.0.0/0
    0     0 ACCEPT     all  --  *      *       0.0.0.0/0            0.0.0.0/0           ctstate RELATED,ESTABLISHED
    0     0 ACCEPT     all  --  *      *       0.0.0.0/0            0.0.0.0/0           state RELATED,ESTABLISHED
  593 46244 ACCEPT     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           tcp dpt:22
    0     0 ACCEPT     all  --  *      *       83.x.x.x             0.0.0.0/0
    0     0 ACCEPT     all  --  *      *       82.x.x.x             0.0.0.0/0
    0     0 ACCEPT     tcp  --  *      *       137.x.x.x            0.0.0.0/0           tcp dpt:80
    0     0 ACCEPT     tcp  --  *      *       137.x.x.x            0.0.0.0/0           tcp dpt:8080
80189 7499K DROP       all  --  *      *       0.0.0.0/0            0.0.0.0/0

Chain FORWARD (policy ACCEPT 0 packets, 0 bytes)
 pkts bytes target     prot opt in     out     source               destination

Chain OUTPUT (policy ACCEPT 962K packets, 508M bytes)
 pkts bytes target     prot opt in     out     source               destination

---

### Post by The Cog on 2010-10-16
Right. Sorry for being grumpy.

The rules look reasonable to me, except for the cstate rule. I don't see anyting wrong with it, but I have a similar iptables setup here and it works fine without needing cstate - the state rule is enough. So there is a (probably insignificant) difference.

My rules also have some forwarding because it's doing some routing, but I guess that's not the case for you. Here are my rules for reference:

```
sudo iptables -nvL
Chain INPUT (policy DROP 188K packets, 18M bytes)
 pkts bytes target     prot opt in     out     source               destination         
  118  5976 ACCEPT     all  --  lo     *       0.0.0.0/0            0.0.0.0/0           
9317K 2542M ACCEPT     all  --  *      *       0.0.0.0/0            0.0.0.0/0           state RELATED,ESTABLISHED 
94656   14M ACCEPT     all  --  *      *       192.168.1.0/24       0.0.0.0/0           
    0     0 ACCEPT     tcp  --  *      *       x.x.x.x        0.0.0.0/0           tcp dpt:22 
    0     0 ACCEPT     tcp  --  *      *       x.x.x.x        0.0.0.0/0           tcp dpt:22 
   13   780 ACCEPT     tcp  --  *      *       x.x.x.x      0.0.0.0/0           tcp dpt:22 
    0     0 ACCEPT     tcp  --  *      *       x.x.x.x         0.0.0.0/0           tcp dpt:22 
 348K   20M ACCEPT     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           tcp dpts:6881:6889 
    0     0 ACCEPT     icmp --  *      *       0.0.0.0/0            0.0.0.0/0           icmp type 8 
  281 14144 ACCEPT     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           tcp dpt:10666 

Chain FORWARD (policy DROP 6 packets, 240 bytes)
 pkts bytes target     prot opt in     out     source               destination         
41796   12M ACCEPT     all  --  *      *       0.0.0.0/0            0.0.0.0/0           state RELATED,ESTABLISHED 
    8   404 ACCEPT     tcp  --  *      *       0.0.0.0/0            192.168.56.2        tcp dpt:22 
 2768  162K ACCEPT     tcp  --  *      *       0.0.0.0/0            192.168.56.2        tcp dpt:80 
 4485  229K ACCEPT     udp  --  *      *       192.168.56.2         192.168.1.1         udp dpt:53 

Chain OUTPUT (policy ACCEPT 12M packets, 7810M bytes)
 pkts bytes target     prot opt in     out     source               destination
```

Things that stand out are that normally, the related,established rule has lots of packets counted, and yours has none. It's possible that this is because you have only ever spoken to the machine from 86.x.x.x - that rule is above the established rule so we wouldn't see established packets counted from that box. It might be useful to re-order the rules to put related,established at the very top of the list and see what happens then - see if they count packets.

I assume these rules are on your server itself, is that right?

What exactly breaks? am I right understanding that your users can connect to the server as you want, but that the server cannot make outgoing connections properly?

I can't see any reason why your server cannot make outgoing connections. Can it even do name loookups - i.e. if you ping [www.google.com](www.google.com) does it try, or say unknown host?

Does your server have more than one LAN connection?

---

### Post by horizonuser on 2010-10-16
@The Cog:

You are correct, I can connect to the server from all the addresses listed but if I try to connect to anywhere from the server the conncetion fails. This is for all traffic e.g ICMP traffic, lookups etc.

I removed the duplicate cstate and moved the ESTABLISHED rule to the top of the chain but the problem remains. It is strange that, as you say, there seems to be no traffic show on that rule. Obviously removing the last DROP rule on the INPUT chain allows access but, like I said, I really can't figure this one out!

---

### Post by The Cog on 2010-10-16
Well, I'm foxed. We agree that it should be working. There's got to be something really odd going on. What could it make it fail to recognise established connections? I'm trying to think of odd things.

It absolutely has to be something inside that server, because nothing outside can tell if that extra line is there in the rules.

You don't have any NAT configured, do you? I'm thinking that maybe somehow some packet mangling is defeating the connection tracking. Though I can't think how.

Perhaps install the conntrack package and run **conntrack -L** to see if any connections are being tracked at all.

I am wondering if there's something wrong with the installation. Perhaps try the same version / different version of OS with the same rules on a spare machine.

And if it were me, I would install wireshark to look at what's happening on the LAN. Just in case something really wacky shows up, although again I can't imagine what. You only need to capture a few packets to see if there's any difference in frinstance doing a ping with and without the rule.

---

