---
title: "Some issues with iptables on web server"
date: 2009-01-21
forum: Security
---

### Post by yamazaki1 on 2009-01-21
Hello everyone, fairly new to Ubuntu and I'm having issues with iptables blocking traffic to my Ubuntu web box (internal).  I'm trying to be pretty painstaking about what ports are allowed in and out and read up on the basic guide to configuring iptables on ubuntu ([https://help.ubuntu.com/community/IptablesHowTo](https://help.ubuntu.com/community/IptablesHowTo))

I set up a pretty tight set of firewall rules, but maybe it's too tight?  I try to open a connection on port 80 or 443 and it doesn't work until I shut down iptables.  If you could review my ruleset it would be most appreciated - did I just miss something completely obvious!?

TIA,
yam

> [FONT="Courier New"]Chain INPUT (policy ACCEPT 0 packets, 0 bytes)
 pkts bytes target     prot opt in     out     source               destination         
    0     0 ACCEPT     all  --  lo     any     anywhere             anywhere            
    4   304 ACCEPT     all  --  any    any     anywhere             anywhere            state RELATED,ESTABLISHED 
    1   100 ACCEPT     tcp  --  any    any     anywhere             anywhere            tcp dpt:ssh 
    0     0 ACCEPT     tcp  --  any    any     anywhere             anywhere            tcp dpt:http 
    0     0 ACCEPT     tcp  --  any    any     anywhere             anywhere            tcp dpt:https 
    0     0 DROP       all  --  any    any     anywhere             anywhere            

Chain FORWARD (policy ACCEPT 0 packets, 0 bytes)
 pkts bytes target     prot opt in     out     source               destination         
    0     0 ACCEPT     all  --  eth0   eth1    anywhere             anywhere            state RELATED,ESTABLISHED 

Chain OUTPUT (policy ACCEPT 0 packets, 0 bytes)
 pkts bytes target     prot opt in     out     source               destination         
    3   748 ACCEPT     all  --  any    any     anywhere             anywhere            state RELATED,ESTABLISHED 
    0     0 ACCEPT     tcp  --  any    any     anywhere             anywhere            tcp dpt:http 
    0     0 ACCEPT     tcp  --  any    any     anywhere             anywhere            tcp dpt:https 
    0     0 ACCEPT     tcp  --  any    any     anywhere             anywhere            tcp dpt:ssh 
    0     0 ACCEPT     tcp  --  any    any     anywhere             anywhere            tcp dpt:domain 
    0     0 ACCEPT     udp  --  any    any     anywhere             anywhere            udp dpt:domain 
    0     0 ACCEPT     udp  --  any    any     anywhere             anywhere            udp dpt:ntp 
    0     0 ACCEPT     udp  --  any    any     anywhere             anywhere            udp dpt:time 
    0     0 ACCEPT     tcp  --  any    any     anywhere             anywhere            tcp dpt:smtp 
    0     0 ACCEPT     tcp  --  any    any     anywhere             anywhere            tcp dpt:smtps 
    0     0 ACCEPT     tcp  --  any    any     anywhere             anywhere            tcp dpt:submission 
    0     0 ACCEPT     tcp  --  any    any     anywhere             anywhere            tcp dpt:webcache 
   81  6932 DROP       all  --  any    any     anywhere             anywhere[/FONT]

---

### Post by yamazaki1 on 2009-01-21
Clarification:  I'm trying to open a connection *to* port 80 on the server from a laptop on the same network so it would use the INPUT chain for port 80 (allowed), and *should* be using the OUTPUT chain and hitting the first rule which allows "RELATED, ESTABLISHED".  Is this a correct assumption?

---

### Post by yamazaki1 on 2009-01-21
Hm, I think I've partially figured this out by using tcpdump.  I'm using mod_rewrite to capture URLs and rewrite http > https in the event that someone tries to access the site over port 80, which should remain open.  Not a big fan of blocking port 80 or sending up an error message saying "Hey maybe you should try typing https in".  Trying to make things as easy as possible on end-users, some of whom may not have the foresight to type up "https" before the URL.

So what I *think* is happening is this:

1) request goes in with src port http (80)
2) Apache intercepts, rewrites the URL to https
3) Apache responds to the request with a src port of https (443), dst port {high_port}
4) iptables blocks the outgoing it as it is not RELATED, ESTABLISHED

Any of you iptables gurus have a nice way around this without just opening up all outbound traffic?

---

### Post by yamazaki1 on 2009-01-21
Hm...I've tried permitting all outbound tcp traffic with sport 80 or 443 so that it doesn't have to be RELATED, ESTABLISHED in order to respond but that doesn't seem to help.

---

### Post by bodhi.zazen on 2009-01-21
I think your problem is with the outbound traffic.

If you are running a server, this line is not doing much for you 

4   304 ACCEPT     all  --  any    any     anywhere             anywhere            state RELATED,ESTABLISHED

In your output, apache uses pseudo random ports on the CLIENT

Thus port xxxx connects to port 80 on the server.

So relax your outbound connections.

You can test this theory by flushing the OUTPUT chain (or changing the default policy to ACCEPT rather then DROP).

Really, blocking OUTPUT is not all *that* necessary, and is a bit harder to do. Sure it helps if you have been cracked, ie blocks say ftp transfers, but as you are allowing http traffic out they can always fall back to wget.

Just my 2c on OUTPUT (I block them too) ;)

You can also see where connections are being dropped if you 

```
sudo itables -l -v
```

flush the counters ```
sudo iptables -z
```

Try to connect to http

then 

```
sudo iptables -L -v
```

---

### Post by yamazaki1 on 2009-01-21
Thanks much bodhi.zazen!  Your input is greatly appreciated and very helpful.  Taking your suggestion I can see that the last rule in my OUTPUT chain is the one that's blocking traffic:

81 6932 DROP all -- any any anywhere anywhere

I was hoping that the first rule in my OUTPUT chain:

ACCEPT all -- any any anywhere anywhere state RELATED,ESTABLISHED

would allow established connections over permitted inbound ports to get outbound traffic out, but apparently that isn't the case and may be a misunderstanding on my part of the rule.  Your comment that it isn't necessary was certainly echoed in my research on this topic!

What I was really hoping for was a policy following something of this nature:

- ALLOW all permitted inbound ports and 
- ALLOW the reflexive outbound traffic to that permitted inbound traffic
- DENY all unwanted inbound ports
- DENY all unwanted outbound ports

The list of ports I do have open outbound (dns, http, https, ntp, & etc.) all require sudo / root access, including wget and the like.  Call me paranoid, I guess ;)

So given this policy I'm attempting to cleave to, is there a clear way to permit inbound https and the outbound traffic back to the requesting client (all on high ports) without just enabling all high ports outbound 100%?

Thanks again,
-yam

---

### Post by bodhi.zazen on 2009-01-21
It will probably work the way you wish if you change your rules (in OUTPUT) from dport to sport

So rather then using:

iptables -A OUTPUT -p tcp **--dport** 22 -j ACCEPT

Use :

iptables -A OUTPUT -p tcp --**sport** 22 -j ACCEPT

---

### Post by yamazaki1 on 2009-01-21
Thanks again bodhi, I tried what you suggested.  I also removed the explicit DROP at the end just so that the http/s connection could complete and I could see what rules it was actually hitting.

I put your suggested rules at the top of my OUTPUT chain, and interestingly they were never hit after clearing the cache and then attempting the https connection:

pkts bytes target     prot opt in     out     source               destination         
  530 69538 ACCEPT     all  --  any    any     anywhere             anywhere            state RELATED,ESTABLISHED 
    0     0 ACCEPT     tcp  --  any    any     anywhere             anywhere            tcp spt:http 
    0     0 ACCEPT     tcp  --  any    any     anywhere             anywhere            tcp spt:https 

I did a tcpdump of the transaction as well and I see that the source port *should* be http / https, but apparently that's not what iptables is seeing...and therefore the rule is never being hit...very strange.

Here's the output of my tcpdump below (routable IPs changed to protect the innocent):

[FONT="Courier New"]23:20:22.272175 IP 10.1.1.1.37261 > 192.168.0.1.http: P 333364473:333364921(448) ack 2962439440 win 65535 <nop,nop,timestamp 835192186 1263239219>
23:20:22.272792 IP 192.168.0.1.http > 10.1.1.1.37261: P 1:630(629) ack 448 win 71 <nop,nop,timestamp 1263251064 835192186>
23:20:22.320119 IP 10.1.1.1.37261 > 192.168.0.1.http: . ack 630 win 65535 <nop,nop,timestamp 835192186 1263251064>
23:20:22.333110 IP 10.1.1.1.38993 > 192.168.0.1.https: P 1584083495:1584083980(485) ack 2970102753 win 65535 <nop,nop,timestamp 835192186 1263239371>
21:25
23:20:22.338465 IP 192.168.0.1.https > 10.1.1.1.38993: P 1:1237(1236) ack 485 win 80 <nop,nop,timestamp 1263251130 835192186>
23:20:22.388077 IP 10.1.1.1.38993 > 192.168.0.1.https: . ack 1237 win 65535 <nop,nop,timestamp 835192187 1263251130>
23:20:22.424055 IP 10.1.1.1.34042 > 192.168.0.1.https: P 1024659541:1024659994(453) ack 2930281302 win 65535 <nop,nop,timestamp 835192187 1263239376>
23:20:22.424279 IP 192.168.0.1.https > 10.1.1.1.34042: P 1:699(698) ack 453 win 121 <nop,nop,timestamp 1263251216 835192187>
23:20:22.427054 IP 10.1.1.1.38993 > 192.168.0.1.https: P 485:986(501) ack 1237 win 65535 <nop,nop,timestamp 835192187 1263251130>[/FONT]

---

### Post by bodhi.zazen on 2009-01-21
Keep in mind that order is important in iptables.

Can we try removing your "ESTABLISHED,RELATED" rule and adding back your DROP (at the bottom of OUTPUT).

Then re-run your (iptables) numbers. I think it will then behave the way you wish.

With your last post, is it working ? Can you connect to the server from your clients?

---

### Post by yamazaki1 on 2009-01-22
I removed the RELATED, ESTABLISHED rules (rule #1) and the two outbound rules for sport 80 and sport 443 were still not being ticked (even though they were first in the chain).  The weird thing is that after I removed the RELATED, ESTABLISHED rule (I used 'iptables -R OUTPUT 1') the following rule was added as rule #1 and started getting hits right away:

1     9012 1498K            all  --  any    any     anywhere             anywhere            

Note that it doesn't have a policy of DROP, ACCEPT, or LOG on it.  Odd.

I decided to try adding the explicit DROP back to the end of the chain (iptables -A OUTPUT -j DROP) and managed to lose my ssh connection to the box.  Hehehe, this will have to wait for morning when I can get a kvm over ;)

---

