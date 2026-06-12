---
title: "iptables firewall logs router"
date: 2011-04-05
forum: Security
---

### Post by ianc1 on 2011-04-05
Hi everyone.  In an effort to learn more about firewalls and iptables I have left behind gui set-up tools and have setup a firewall using iptables that logs to its own file.  The firewall is as follows:
```
*filter
:INPUT DROP [0:0]
:FORWARD DROP [0:0]
:OUTPUT ACCEPT [0:0]
:TCP - [0:0]
:UDP - [0:0]
-A INPUT -i lo -j ACCEPT 
-A INPUT -m conntrack --ctstate INVALID -j LOG --log-prefix "iptables denied: " --log-level 7
-A INPUT -m conntrack --ctstate INVALID -j DROP 
-A INPUT -m conntrack --ctstate RELATED,ESTABLISHED -j ACCEPT 
-A INPUT -p icmp -m icmp --icmp-type 8 -m conntrack --ctstate NEW -j ACCEPT 
-A INPUT -p udp -m conntrack --ctstate NEW -j UDP 
-A INPUT -p tcp -m tcp --tcp-flags FIN,SYN,RST,ACK SYN -m conntrack --ctstate NEW -j TCP 
-A INPUT -p udp -j REJECT --reject-with icmp-port-unreachable 
-A INPUT -p tcp -j REJECT --reject-with tcp-reset 
-A INPUT -j LOG --log-prefix "iptables failed, denied: " --log-level 7
-A INPUT -j REJECT --reject-with icmp-proto-unreachable 
COMMIT
```In the log file I get messages saying my router sent a packet that got through all the rules to the end and was then rejected.  After the interface, mac address and source ip address the following is listed ```
LEN=36 TOS=0x00 PREC=0xC0 TTL=1 ID=8290 DF PROTO=2
```This is being logged roughly every minute.  How do I stop it, can I simply insert a rule to allow my routers IP address or does this create a hole/backdoor access for someone.

Thanks

---

### Post by Doug S on 2011-04-06
Hi ianc,

I was wondering how you were doing with your iptables rules (see other thread "help with iptables-save" (which could probably be set to solved)).

Your rule set looks a just a little odd, in that I don't understand your TCP and UDP tables, or why they are there. I do not see any rules added to each one.

REJECT verses DROP: (at the risk of sparking a debate) By far, most unsolicited incoming packets are from vulnerability probes. My suggestion is to just DROP them. By REJECTing them you are telling the source that you are there and are listening.

To try to answer your actual question: Without knowing more, it is hard to say. It is good to have a catch all rule at the end of your chain. It is also good to attempt to never have packets actually get there, because that means we really understand, and have covered, all of the cases. My guess (based on length and TTL) is that the packets are IGMP packets from your router. On one of my routers, I have been unsuccessful in getting that stuff turned off (even though there is a setting that says it will turn it off). You can ignore those packets. If you do decide to let them through, I don't think your create a hole or backdoor. ( I read up on IGMP one time but have since forgotten)

---

### Post by bodhi.zazen on 2011-04-06
> **Doug S said:**
> REJECT verses DROP: (at the risk of sparking a debate) By far, most unsolicited incoming packets are from vulnerability probes. My suggestion is to just DROP them. By REJECTing them you are telling the source that you are there and are listening.

DROP and REJECT are equally secure (or at least equally debated without a conclusive answer to which is more or less secure). Both close the port.

REJECT is a bit more polite =)

One still knows you are there if you use DROP, try it with nmap (only scan your own box).

On a test client, use a simple set of rules

```
sudo iptables -F
sudo iptables -X
sudo iptables -P INPUT DROP
sudo iptables -P OUTPUT DROP
```

That will set the default policy on the test box to drop all traffic.

The hit it with nmap from a second box. You will see the clinet is "up".

I have a detailed output of just such a scan somewhere here.

As long as you are connected to the internet, it is difficult or impossible to "hide" your ip.

---

### Post by ianc1 on 2011-04-06
Hi Doug S.  Firstly, sorry, I had neglected to get back to my ealier post and thanks to you and everyone else who replied.  It's now marked as solved.

I had based the firewall on one in the Arch wiki.  The TCP and UDP tables are where I was going to add rules to accept TCP or UDP packets as I wanted.  Ie if I discovered I need TCP from a certain IP address I could add an ACCEPT rule in the TCP table.  My understanding is that```
-A INPUT -p udp -m conntrack --ctstate NEW -j UDP
-A INPUT -p tcp -m tcp --tcp-flags FIN,SYN,RST,ACK SYN -m conntrack --ctstate NEW -j TCP
```send udp and tcp packets respectively to the UDP and TCP tables.

I also understand that if these tables are empty the firewall then goes back to the INPUT table to carry out the next rule and if that isn't met the next one until the end.  Hence, my DROP and LOG rules at the end.  At present the TCP and UDP tables are as you pointed out empty and therefore doing nothing, but I thought it was doing no harm.  Am I correct or seriously misguided.

Would the best bet to get rid of these logged packets be to add one of the following:```
iptables -A INPUT -p igmp -j DROP
iptables -A INPUT -p igmp -j REJECT
iptables -A INPUT -p igmp -j ACCEPT
```I assume they're my routers way of checking my PC is still up and running.[FONT=monospace]

I had already tried nmap as [/FONT]bodhi.zazen pointed out and it does indeed find the PC.

Thanks for the help guys.  Any further comments would be much appreciated.

---

### Post by bodhi.zazen on 2011-04-06
I would eiterh reduce your log lever ( 7 is quite verbose) or add a rule to rate limit the log ;)

--log-level 7 -m limit --limit 1/hour --limit-burst 2

---

### Post by Doug S on 2011-04-06
bodhi.zazen:

Far enough, nmap, or anybody else, can determine that a site is there via the arp packet. However, I rarely, if ever, see an arp packet with the more generic probing that is always going on. Below is a tcpdump fragment from the experiment you suggested on my test client, where nmap does the arp packet followed by a few lines of its port scanning:

```
 
2011-04-06 13:01:54.836308 arp who-has 192.168.111.140 (ff:ff:ff:ff:ff:ff) tell 192.168.111.100
2011-04-06 13:01:54.836536 arp reply 192.168.111.140 is-at 00:50:ba:4d:0a:3f
2011-04-06 13:01:54.847177 arp who-has 192.168.111.1 tell 192.168.111.100
2011-04-06 13:01:55.043448 IP 192.168.111.100.42242 > 192.168.111.140.443: S 1132711220:1132711220(0) win 3072 <mss 1460>
2011-04-06 13:01:55.043949 IP 192.168.111.100.42242 > 192.168.111.140.199: S 1132711220:1132711220(0) win 3072 <mss 1460>
2011-04-06 13:01:55.044292 IP 192.168.111.100.42242 > 192.168.111.140.8888: S 1132711220:1132711220(0) win 4096 <mss 1460>
```

I agree that there is no security difference between REJECT and DROP. I also agree that REJECT is more polite. However (and this is just my own preference here, nothing more) I prefer DROP for two additional reasons: First, because I am not concerned about being polite to the probers and hackers; Second, merely to try to minimize useless packets on internet.

By the way, I think you need to specify a chain with the"-P" option in iptables, as it will not allow a global set them all in one command.  I.E. "sudo iptables &#8211;P INPUT DROP"
ianc:

Thanks for explaining, now I understand. I would just DROP packets from your router. I don't know if there is a protocol "igmp" for checking, but I didn't look very hard. If not it could be done via direct byte matching within the packet (difficult, but I could help (later, I am out of time just now), or maybe you could detect and drop by source IP (I don't know what other reasons you have for router communications, so maybe that is a bad idea).

---

### Post by bodhi.zazen on 2011-04-06
There is nothing wrong with DROP, and I did not intend to come across as confrontational. I tend to use DROP myself for reasons similar to what you cited.

I merely wanted to correct what I think is a common misconception about DROP and your visibility (it is IMO propagated by the term "stealth" on a certain web site, lol) or security of DROP (vs REJECT).

I think it is more important to explain DROP and REJECT rather then propagate misconceptions.

Security is a balance between convenience and hassle, so while DROP is a hassle to would be crackers, REJECT is appreciated by legitimate traffic.

It sort of depends on if you are running a public server (http) or private (ssh) and your proportion of legitimate to illegitimate traffic.

---

### Post by bodhi.zazen on 2011-04-06
> **Doug S said:**
> By the way, I think you need to specify a chain with the"-P" option in iptables, as it will not allow a global set them all in one command.  I.E. "sudo iptables –P INPUT DROP"

/me bad, I updated my post.

---

### Post by ianc1 on 2011-04-06
Thanks Doug S and bodhi.zazen my problem is now solved and I've learnt a lot as well, thanks.

I inserted a rule to DROP the igmp packets (which turns out to be protocol 2) at the top the table just below the loopback rule.

I quite like the log level of 7 as it gives everything I could want and some info I don't understand but is making me look into these extra bits and learn more.  Its quite interesting who sends bucket loads of packets at you for example today and I have had packets every second for a phase from a wikimedia site and a university in the states all failing on```
iptables -A INPUT -m conntrack --ctstate INVALID -j DROP
```The web must be slowing down with all this junk.  I don't want these packets and what are they trying to gain from me?

I can see some filtering and rule optimization is required, although they have been stopped.

Thanks again.

---

