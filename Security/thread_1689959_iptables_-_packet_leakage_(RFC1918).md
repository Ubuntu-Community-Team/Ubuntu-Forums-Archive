---
title: "iptables - packet leakage (RFC1918)"
date: 2011-02-17
forum: Security
---

### Post by Doug S on 2011-02-17
I am using Ubuntu server version 10.10 64 bit with two network interface cards (NIC).
I have an iptables rules set that started out based on the generally available "rc.firewall-iptables-stronger" version 0.88s, included in some IPTABLES-howto notes.
 
One of the issues I had was packet leakage (I am calling it) where packets were escaping to internet without Network Address Translation. For example, a packet would go out to internet as being from 192.168.111.100 instead of appearing to be from 209.121.28.192 (smythies.com). As per RFC1918, I thought is was poor form for such packets to be sent to out. In terms of this security forum, it also meant that details about my internal network were being sent out. The packets were always TCP and always the result of a half closed TCP session where the CLOSE_WAIT time had expired, and conntrack had forgotten about the session. I was able to prevent the packet leakage by the addition of one line to the iptables rule set at the start of the forward chain:
 
$IPTABLES -A FORWARD -i $INTIF -p tcp -m state --state INVALID -j DROP
$IPTABLES -A FORWARD -i $EXTIF -o $INTIF -m state --state ESTABLISHED,RELATED -j ACCEPT
$IPTABLES -A FORWARD -i $INTIF -o $EXTIF -j ACCEPT
 
 
My question and or concern is: Even without the fix rule that I added shouldn't the packets that went out through the forward chain have gone through address translation?
 
I realize that some readers might want more information. Although still a little rough, my complete investigation notes, and iptables script is at:
 
[http://www.smythies.com/~doug/network/iptables_notes/index.html](http://www.smythies.com/~doug/network/iptables_notes/index.html) 
 
And, yes, I am aware that releasing such detail about my network is security issue in itself. (I will probably change my internal network addresses).

---

### Post by gmargo on 2011-02-17
Interesting, and I like your write up.

I don't have an answer sadly.  But thought I would mention, that back when I was doing my own firewalling, I always added a rule, on the output chain for the external interface, that would drop (and log) any "[martian packets]("http://en.wikipedia.org/wiki/Martian_packet")".

---

### Post by Doug S on 2011-02-17
An outgoing check for "martian" packets is a good idea. It would protect against mistakes while experimenting and such. However, I was not able to make such additional rules work (they are still in my iptables script, but are commented out). I am not aware of a way in iptables to check that the after NAT (Network Address Translation) address is non-martian. In other words I am not aware of a way to check that the source address that will appear on internet is 209.121.28.192 (in my case). As far as I know, any source address check in iptables refers to the original input source address. I hope I am wrong and there is a way.
 
I assume that I can set the eth1 (in my case) martian check listed below to 1 to log an escaping martian packet, but I don't think it also drops the packet (but I don't know for sure, and will test it).
 
```
 
sudo sysctl -a | grep martians
net.ipv4.conf.all.log_martians = 0
net.ipv4.conf.default.log_martians = 0
net.ipv4.conf.lo.log_martians = 0
net.ipv4.conf.eth0.log_martians = 0
net.ipv4.conf.eth1.log_martians = 0   <<<< Here

```

---

### Post by SeijiSensei on 2011-02-17
I'm puzzled.

First, RFC1918 packets aren't routable over public networks, so I don't understand how any of them could migrate beyond your doorstep.  Even if they were sent upstream to your next-hop router, they'd be ignored.  I've done that myself a number of times while trying to set up routing or firewalling.  If the packets carry a private source address, they'll be dropped.

Second, where does the network address translation take place?  Here, for instance, are my rules:

```

iptables -A FORWARD -i $INTI -o $EXTI -j ACCEPT
iptables -t nat -A POSTROUTING -o $EXTI -j SNAT --to $EXT

```

INTI and EXTI are the internal and external interfaces (eth1 and eth0, respectively) and EXT is my external IP address.  This tells iptables to rewrite the source address of any packet intended for the external interface with the firewall's external address.   There's no room for "leakage" here that I can see.

If your NAT rules rely on IP addresses rather than interfaces, it would be possible to use an incorrect subnet or mask so that some packets wouldn't match the rule.  Still, if they have an RFC1918 address, they aren't going to get past that next-hop router no matter what.

---

### Post by Doug S on 2011-02-18
Sorry, I only listed my FORWARD chain rules in my original post. My postrouting rule is identical to that of SeijiSensei:
 
```
 
$IPTABLES -t nat -A POSTROUTING -o $EXTIF -j SNAT --to $EXTIP


```
 
I think that the leakage packets can get to the destination as it is the untranslated source IP address that is unroutable, not the desination address.
 
So the question might be asked, how then would the desination know that the packet came from my system and therefore learn something about my internal network addresses. Via port numbers. For example (from my web notes write up), consider a web browser session from 192.168.111.106 on port 52181 to 174.35.52.137 port 80. After conntrack forgets about the TCP session, 192.168.111.106 sends more packets from port 52181 which go through without Network Address Translation but with the same port number. If it were monitoring packets, and if the packets get there, the destination could realize what is going on (I would). O.K. I admit, it is a bit of a reach to claim that this is a real security issue. However, I still think my orignal posting question/concern is valid.

---

### Post by SeijiSensei on 2011-02-18
> **Doug S said:**
> I think that the leakage packets can get to the destination as it is the untranslated source IP address that is unroutable, not the desination address.

The routers upstream from you will drop packets with a private source address regardless of the destination address.

---

### Post by Doug S on 2011-02-19
Please bear with me while I to understand. If the upstream routers will drop any packets with private source IP address regardless of the destination IP address then wouldn't it also be the case that I should never see such packets arriving at my site?
 
Wouldn't that mean that I should not need iptables INPUT chain rules to check for and drop such packets? Wouldn't it also mean that the counters for those rules should always stay at 0? (At my site the counters do not stay at 0).
 
For example, shouldn't these packets never have arrived at my site?:
 
```
 
2011-01-23 17:00:42.809626 IP 192.168.5.80 > 209.121.28.192: ICMP echo request, id 512, seq 49943, length 8
2011-01-30 04:48:02.380712 IP 192.168.218.104.12399 > 209.121.28.192.22: Flags [S], seq 1591824635, win 65535, options [mss 1460,nop,nop,sackOK], length 0
2011-02-06 23:47:00.485650 IP 10.21.0.254 > 209.121.28.192: ICMP net 130.177.222.244 unreachable, length 36
2011-02-06 23:47:03.131181 IP 10.21.0.254 > 209.121.28.192: ICMP net 130.177.222.244 unreachable, length 36
2011-02-10 21:50:38.220779 IP 10.161.17.244 > 209.121.28.192: ICMP echo request, id 512, seq 2582, length 8
2011-02-15 15:10:36.630601 IP 192.168.110.9.2516 > 209.121.28.192.80: Flags [S], seq 953903204, win 65535, options [mss 1460,nop,nop,sackOK], length 0


```

---

### Post by SeijiSensei on 2011-02-19
You should ask your ISP about this.

---

### Post by Doug S on 2011-04-05
Setting this one to solved. It is not actually solved, but I think it is a question for netfilter.org, where two similar bugzilla bugs were already posted:
[URL="http://bugzilla.netfilter.org/show_bug.cgi?id=693"]
http://bugzilla.netfilter.org/show_bug.cgi?id=693[/URL]
[URL="http://bugzilla.netfilter.org/show_bug.cgi?id=627"]
http://bugzilla.netfilter.org/show_bug.cgi?id=627[/URL]

I added some notes to #693.

For the other debate within this thread: Does one need to worry about the leakage packets anyhow? I feel a responsibility to only send "good" packets out onto into internet. I would not want to rely on upstream packet handlers to filter out my mess. However, and as SeijiSensei  points out, there is likely no harm in sending out the non-routable return address packets anyhow.
By the way, I am now always running with a CLOSE_WAIT time of 3600 seconds instead of the default of 60 seconds. On my network it reduces the number of leakage packets (or invalid packets detected by the iptables rule) by a factor of between 10 and 100, without noticeably growing the conntrack table.

---

