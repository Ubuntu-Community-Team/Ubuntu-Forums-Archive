---
title: "How does Squid handle bandwidth distribution"
date: 2009-06-17
forum: Server Platforms
---

### Post by marklodge on 2009-06-17
Can squid do 'fair bandwidth sharing' ? 
What i mean is, if there is 1 user online on a 4mg line, that user will  be using the entire 4mg line speed, and if there are 2 users online,  each user will have 2mg line speed, and so on. 
I have squid cache set up already, but i just need to know how bandwidth  distribution/sharing can be handled 

Can squid also be used to limit/disconnect users after they have used up  their allotted bandwidth? 

[I have a mikrotik router connected to the adsl (for wireless users)] 

I would really appreciate your comments and help 
Thank you

---

### Post by ghen on 2009-06-17
Here's what I found on google searching for Squid Bandwidth. It definitely looks like squid can do it, but I don't know how effective it will be since its not done at the packet layer. (AFAIK)

[http://www.faqs.org/docs/Linux-HOWTO/Bandwidth-Limiting-HOWTO.html](http://www.faqs.org/docs/Linux-HOWTO/Bandwidth-Limiting-HOWTO.html)

---

### Post by marklodge on 2009-06-17
> **ghen said:**
> Here's what I found on google searching for Squid Bandwidth. It definitely looks like squid can do it, but I don't know how effective it will be since its not done at the packet layer. (AFAIK)

[http://www.faqs.org/docs/Linux-HOWTO/Bandwidth-Limiting-HOWTO.html](http://www.faqs.org/docs/Linux-HOWTO/Bandwidth-Limiting-HOWTO.html)


Thanks for the reply, but thats not exactly what i had in mind, the closest info to what i require in the link you provided was: 
**5.13. CBQ is stupid; why can't I download something at full speed when the network is used only be me?**

**[SIZE=3]But, this is only giving us the solution of disabling it from 1am to 7am[/SIZE]**

I need something dynamic, so when there is 1 user using the network, he gets it full speed, if 10 users are using it they each get a fair share of the speed.

Would appreciate your help



****

---

### Post by grantemsley on 2009-06-17
That kind of stuff is better handled by QOS, though I don't know of any implementations that do it exactly the way you are describing.

Besides, if there are two users, user 1 is downloading a large file, and user 2 is checking their email...does it really make sense to limit them both to 2mbit/s?  I'd think the better thing to do is prioritize the email traffic, so it gets whatever speed it needs, and the downloader gets whatever is left over.

---

### Post by HermanAB on 2009-06-17
Here you go:
[http://lartc.org/](http://lartc.org/)

15.9. Rate limiting a single host or netmask

Although this is described in stupendous details elsewhere and in our manpages, this question gets asked a lot and happily there is a simple answer that does not need full comprehension of traffic control.

This three line script does the trick:

	  tc qdisc add dev $DEV root handle 1: cbq avpkt 1000 bandwidth 10mbit 

	  tc class add dev $DEV parent 1: classid 1:1 cbq rate 512kbit \
	  allot 1500 prio 5 bounded isolated 

	  tc filter add dev $DEV parent 1: protocol ip prio 16 u32 \
	  match ip dst 195.96.96.97 flowid 1:1
	

The first line installs a class based queue on your interface, and tells the kernel that for calculations, it can be assumed to be a 10mbit interface. If you get this wrong, no real harm is done. But getting it right will make everything more precise.

The second line creates a 512kbit class with some reasonable defaults. For details, see the cbq manpages and Chapter 9.

The last line tells which traffic should go to the shaped class. Traffic not matched by this rule is NOT shaped. To make more complicated matches (subnets, source ports, destination ports), see Section 9.6.2.

If you changed anything and want to reload the script, execute 'tc qdisc del dev $DEV root' to clean up your existing configuration.

The script can further be improved by adding a last optional line 'tc qdisc add dev $DEV parent 1:1 sfq perturb 10'. See Section 9.2.3 for details on what this does. 



9.6.2. All the filtering commands you will normally need

Most shaping commands presented here start with this preamble:

# tc filter add dev eth0 parent 1:0 protocol ip prio 1 u32 ..

These are the so called 'u32' matches, which can match on ANY part of a packet.

On source/destination address

    Source mask 'match ip src 1.2.3.0/24', destination mask 'match ip dst 4.3.2.0/24'. To match a single host, use /32, or omit the mask.
On source/destination port, all IP protocols

    Source: 'match ip sport 80 0xffff', destination: 'match ip dport 80 0xffff'
On ip protocol (tcp, udp, icmp, gre, ipsec)

    Use the numbers from /etc/protocols, for example, icmp is 1: 'match ip protocol 1 0xff'. 
On fwmark

    You can mark packets with either ipchains or iptables and have that mark survive routing across interfaces. This is really useful to for example only shape traffic on eth1 that came in on eth0. Syntax:

    # tc filter add dev eth1 protocol ip parent 1:0 prio 1 handle 6 fw flowid 1:1

    Note that this is not a u32 match!

    You can place a mark like this:

    # iptables -A PREROUTING -t mangle -i eth0 -j MARK --set-mark 6

    The number 6 is arbitrary.

    If you don't want to understand the full tc filter syntax, just use iptables, and only learn to select on fwmark.
On the TOS field

    To select interactive, minimum delay traffic:

    # tc filter add dev ppp0 parent 1:0 protocol ip prio 10 u32 \
          match ip tos 0x10 0xff \
         flowid 1:4

    Use 0x08 0xff for bulk traffic.

For more filtering commands, see the Advanced Filters chapter.

---

