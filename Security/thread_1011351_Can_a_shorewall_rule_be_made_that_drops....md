---
title: "Can a shorewall rule be made that drops..."
date: 2008-12-14
forum: Security
---

### Post by Gen2ly on 2008-12-14
Can a shorewall rule be made that drops spoofed ip addresses that belong to me?  I've been getting data lately that appears to be attacks with the source address belonging to... myself.  Is there a way a shorewall rule can be created that drop ip owned spoof attacks?

---

### Post by HermanAB on 2008-12-15
I believe Shorewall already does that.

However, such a rule is very simple:
iptables -I INPUT -i eth0 -s your.machine.ip.address -j DROP

That will drop packets coming in on your ethernet device, with a source being your own IP address.  You should read 'man iptables' about 5 times - it will eventually make some sense and is well worth the time investment in the long run.

Hope that helps!

Cheers,

Herman

---

### Post by Gen2ly on 2008-12-15
lol, I think I'm getting it.  thanks for the help.

---

### Post by Gen2ly on 2008-12-15
NOT WORKING!!!!!  Holy cow I've had around 40 port scans spoofed as my IP this afternoon, a TCP port sweep and a couple OVERSIZE REQUEST-URI DIRECTORY.  Can anyone help me?

---

### Post by HermanAB on 2008-12-15
It has to work - provided that you insert the rule at the top of the list (-I).  You can list the existing rules with "iptables -L".  Then test it from another machine.

---

### Post by The Cog on 2008-12-15
I think what HermanAB wrote should work. What makes you think it doesn't?

---

### Post by Gen2ly on 2008-12-15
hmm... this has me confused too.

from snort:

```
...
#111-(7-56) 	 [snort] (portscan) Open Port: 80
	2008-12-15 15:58:30 	24.xxx.yy.38 	72.233.2.59 	Raw IP
	#112-(7-57) 	[snort] (portscan) Open Port: 80
	2008-12-15 15:58:30 	24.xxx.yy.38 	72.233.2.59 	Raw IP
	#113-(7-58) 	[snort] (portscan) Open Port: 80
	2008-12-15 15:58:30 	24.xxx.yy.38 	66.114.53.35 	Raw IP
	#114-(7-59) 	[snort] (portscan) Open Port: 80
	2008-12-15 15:58:30 	24.xxx.yy.38 	72.233.2.59 	Raw IP
	#115-(7-60) 	[snort] (portscan) Open Port: 80
	2008-12-15 15:58:31 	24.xxx.yy.38 	72.233.2.59
```

And iptables shows the drop:

```
iptables -nvL
Chain INPUT (policy DROP 0 packets, 0 bytes)
 pkts bytes target     prot opt in     out     source               destination                                                                                   
    0     0 DROP       all  --  eth0   *       24.xxx.yy.38         0.0.0.0/0                                                                                     
 281K  399M dynamic    all  --  *      *       0.0.0.0/0            0.0.0.0/0                                                                                     
 274K  396M net2fw     all  --  eth0   *       0.0.0.0/0            0.0.0.0/0                                                                                     
 6407 2674K ACCEPT     all  --  lo     *       0.0.0.0/0            0.0.0.0/0                                                                                     
    0     0 ACCEPT     all  --  *      *       0.0.0.0/0            0.0.0.0/0           state RELATED,ESTABLISHED                                                 
    0     0 Drop       all  --  *      *       0.0.0.0/0            0.0.0.0/0                                                                                     
    0     0 LOG        all  --  *      *       0.0.0.0/0            0.0.0.0/0           LOG flags 0 level 6 prefix `Shorewall:INPUT:DROP:'                        
    0     0 DROP       all  --  *      *       0.0.0.0/0            0.0.0.0/0                                                                                     
    0     0 DROP       all  --  eth0   *       24.xxx.yy.38         0.0.0.0/0 
```

Could this be an attack from the internal network possibly?  Or (hopefully) the packets are being dropped and snort see them still!?

I appreciate the help guys this is a little beyond my network experience.

---

### Post by HermanAB on 2008-12-15
I don't know where Snort hooks into the network stack.  You'll have to read up on the Snort and Netfilter web sites if you want to understand it.

---

### Post by The Cog on 2008-12-16
I take it that 24.xxx.yy.38 is your own machines address?

It may be that the machine is doing reverse path filtering before the packets even reach iptables. I don't know the order that filtering is applied, or even if it is used at all for packets addressed to the machine rather than packets being routed.
You can see if rp filtering is enabled with this command:
> cat /proc/sys/net/ipv4/conf/default/rp_filter
and can turn it on / off by:
> echo 1 > /proc/sys/net/ipv4/conf/default/rp_filter
echo 0 > /proc/sys/net/ipv4/conf/default/rp_filter
which might be interesting to see if doing so affects whether those iptables rules count any hits.

---

### Post by Gen2ly on 2009-01-02
Would it make any difference if the attacks are coming from my isp?  Could those attacks be disguised?

---

### Post by The Cog on 2009-01-03
I don't think it matters who is sending them. But as HermanAB implied, short may be seeing the packets before they are dropped by the IP stack. I am fairly sure that wireshark captures packets that then get dropped by iptables, and I guess short uses the same packet capture facility. In which case snort will be able to see and report on packets that iptables promptly drops.

---

### Post by Gen2ly on 2009-01-10
Good tips Cog.  You are right I read some documetation and snort will see the packets even if filtered by iptables.  I am still having problems and got hacked.  My best and wild guess is that the attacks are coming from the DNS server itself.  It's only a guess and could be wrong but that the DNS server is able to circumvent this.  Hey, its the best I got. :) ... blocking my own ip didn't help.  Looks like I'll be thinking about buying a firewall box.  Appreciate the help.

---

### Post by Gen2ly on 2009-02-22
yeah, i figured this out.  my isp is packet-injecting into already established connections from my web browser (e.g <my-ip:50022>).  It's a good isp and a big big company.  one bad-apple in the company is all it takes.  probably the best thing to do is report this to the company and hope they will ferret this out.  Otherwise itmight be possible to create a rule in snort that drops the packet!?

---

