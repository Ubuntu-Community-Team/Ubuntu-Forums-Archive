---
title: "Iptables rule help"
date: 2013-06-26
forum: Security
---

### Post by linuxcenter on 2013-06-26
**Rule 1: want to block all Incoming/Input connections,** from port range 0 to 65535.
**Rule 2: In Outgoing/Output allow only tcp port 80,443, udp 53 **& block all the remaining ports 0 to 65535

Additional rules for:
[B]blocking ping attempts
blocking dos attacks
blocking script attacks[/B] O:)

---

### Post by CharlesA on 2013-06-26
Have a read:
[http://bodhizazen.net/Tutorials/iptables](http://bodhizazen.net/Tutorials/iptables)

---

### Post by JKyleOKC on 2013-06-26
> **linuxcenter said:**
> **Rule 1: want to block all Incoming/Input connections,** from port range 0 to 65535.If you actually implement such a rule, you will be unable to do anything on the internet. If you block **all** input connections, that will prevent your receipt of **any** reply to **any** of your outgling packets. For example, you could attempt to connect to google.com, but you would not receive the DNS reply that told you the address of Google, much less receive any reply from your http connection message.

If the intent is to block all unsolicited input traffic, you need a rule to ACCEPT packets with status RELATED or ESTABLISHED, like this: ```
-A INPUT -i eth0 -m state --state RELATED,ESTABLISHED -j ACCEPT
``` Follow it with a second rule to DROP everything else: ```
-A INPUT -j DROP
```

The tutorial that CharlesA referred you to is very good, but "iptables" is sufficiently complicated that any attempt to cover it is going to be massively confusing at the start. The best bet, if you want to roll your own set of rules, is to tackle one goal at a time and make sure that it's doing what you want before moving on to the next...

---

### Post by CharlesA on 2013-06-26
> **JKyleOKC said:**
> 
The tutorial that CharlesA referred you to is very good, but "iptables" is sufficiently complicated that any attempt to cover it is going to be massively confusing at the start. The best bet, if you want to roll your own set of rules, is to tackle one goal at a time and make sure that it's doing what you want before moving on to the next...

That is how I learned iptables (and locked myself out on more than one occasion...). If you are going to be dealing with firewall rules be sure you have console access to the machine in question.

sidenote: I use REJECT instead of DROP so I don't have to sit there wondering why I keep getting timeout messages when troubleshooting.

See here: [http://www.chiark.greenend.org.uk/~peterb/network/drop-vs-reject](http://www.chiark.greenend.org.uk/~peterb/network/drop-vs-reject)

---

### Post by Hungry Man on 2013-06-26
Instead of removing ALL inbound traffic, try...

[COLOR=#404040][FONT=Open Sans]*iptables -A INPUT -m state &#8211;state RELATED,ESTABLISHED -j ACCEPT*[/FONT][/COLOR]
[COLOR=#404040][FONT=Open Sans]*iptables -A INPUT  -m state &#8211;state NEW -p udp &#8211;dport 53 -j ACCEPT*[/FONT][/COLOR]
[COLOR=#404040][FONT=Open Sans][I]iptables -A INPUT -m  state &#8211;state NEW,INVALID -j REJECT

[/I][/FONT][/COLOR]This prevents all inbound access EXCEPT for:
1) When traffic is solicited by a previous outbound connection
2) To port 53 using UDP, which will allow your DNS resolution.

For your second request:


iptables -A OUTPUT -p tcp -m multiport --dports 443,80 -j ACCEPT
iptables -A OUTPUT -p udp -m udp --dport 53 -j ACCEPT
iptables -A OUTPUT -m owner -j DROP

For the others:
You'll need more complicated time-based rulesets. I'm too lazy. Try fail2ban, maybe.

---

### Post by Hungry Man on 2013-06-26
Instead of removing ALL inbound traffic, try...

[COLOR=#404040][FONT=Open Sans]*iptables -A INPUT -m state &#8211;state RELATED,ESTABLISHED -j ACCEPT*[/FONT][/COLOR]
[COLOR=#404040][FONT=Open Sans]*iptables -A INPUT  -m state &#8211;state NEW -p udp &#8211;dport 53 -j ACCEPT*[/FONT][/COLOR]
[COLOR=#404040][FONT=Open Sans][I]iptables -A INPUT -m  state &#8211;state NEW,INVALID -j REJECT

[/I][/FONT][/COLOR]This prevents all inbound access EXCEPT for:
1) When traffic is solicited by a previous outbound connection
2) To port 53 using UDP, which will allow your DNS resolution.

For your second request:


iptables -A OUTPUT -p tcp -m multiport --dports 443,80 -j ACCEPT
iptables -A OUTPUT -p udp -m udp --dport 53 -j ACCEPT
iptables -A OUTPUT -m owner -j DROP

For the others:
You'll need more complicated time-based rulesets. I'm too lazy. Try fail2ban, maybe.

---

### Post by SeijiSensei on 2013-06-27
Regardless of what you choose, you almost always need to to enable traffic on the localhost interface.

```
/sbin/iptables -A INPUT -i lo -j ACCEPT
```

---

### Post by Doug S on 2013-06-27
> **Hungry Man said:**
> Instead of removing ALL inbound traffic, try...

[COLOR=#404040][FONT=Open Sans]*iptables -A INPUT -m state –state RELATED,ESTABLISHED -j ACCEPT*[/FONT][/COLOR]
[COLOR=#404040][FONT=Open Sans]*iptables -A INPUT  -m state –state NEW -p udp –dport 53 -j ACCEPT*[/FONT][/COLOR]
[COLOR=#404040][FONT=Open Sans][I]iptables -A INPUT -m  state –state NEW,INVALID -j REJECT

[/I][/FONT][/COLOR]This prevents all inbound access EXCEPT for:
1) When traffic is solicited by a previous outbound connection
2) To port 53 using UDP, which will allow your DNS resolution.
...You do not need the specific --dport 53 line. Outgoing DNS requests will: get back via the RELATED,ESTABLISHED line; not be to port 53 anyway (they will be from a port 53).

---

### Post by Hungry Man on 2013-06-27
It's necessary on my system, but I use a different resolver, so that may be why.

---

### Post by Kujua on 2013-06-27
> **Hungry Man said:**
> It's necessary on my system, but I use a different resolver, so that may be why.
Is your host acting as DNS server for other hosts? If not, opening port 53 is not the right way to go.
If you want your DNS queries to go through your resolver, you should be allowing connections only from localhost. Like SeijiSensei suggested above, you should not block traffic on lo.

---

### Post by Hungry Man on 2013-06-27
I'm using DNSCrypt, and I have it running as a separate user. It needs outbound access. I used a rule to stop all inbound access that is NEW/INVALID and it stopped resolving. So I added an inbound rule for UDP on 53, now it works.

---

### Post by JKyleOKC on 2013-06-27
If you put the allow-all for the loopback interface lo, as suggested in post #7 above, you won't need the port 53 rule. Doing it as you currently are allows anyone on the internet to get into your system via port 53, but your local resolver running as a different user will use the loopback interface (which as the name implies simply loops output back to input without ever going outside your system) and so won't be trapped by the "NEW,INVALID" rule.

Even better, perhaps, would be to add the "-i eth0" or "-i wan0" parameter to your three INPUT rules, so that they apply only to the specific interface that connects to the outside world. There are many many ways to remove the fur from the feline, when dealing with iptables -- which is part of why it can be so confusing.

---

### Post by Hungry Man on 2013-06-27
Interesting. Thank you.

---

### Post by linuxcenter on 2013-06-30
Thank You to ALL  :)

---

### Post by linuxcenter on 2013-06-30
.

---

### Post by linuxcenter on 2013-06-30
.

---

### Post by linuxcenter on 2013-06-30
[SIZE=4]OK How about these rules ? [/SIZE]


**[COLOR=#0000cd]Rule 1: want to block all Incoming/Input connections, from port range 0 to 65535.[/COLOR]**

**iptables -A INPUT ****[B]-p tcp -m multiport --sports 0-65535 --dports 0-65535** -j DROP

[COLOR=#0000cd]Rule 2: In Outgoing/Output allow only tcp port 80,443, udp 53 & block all the remaining ports 0 to 65535[/COLOR]

iptables -A OUTPUT -p tcp -m multiport --sports 80,443 -d 0/0 --dports 80,443 -m state --state NEW,ESTABLISHED -j ACCEPT

[/B][B]iptables -A OUTPUT -p udp -m multiport --sports 53 --dports 53 -m state --state NEW,ESTABLISHED -j ACCEPT
[/B]
**iptables -A OUTPUT -j DROP**


=======================================================================

**blocking ping attempts**
iptables -A OUTPUT -p icmp --icmp-type echo-request -j DROP

**blocking dos attacks**

iptables -A INPUT -p udp -m state --state NEW -m recent --update --seconds 1 --hitcount 5 --name DDOS --rsource -j DROP

:KS:KS:KS:KS:KS

---

### Post by SeijiSensei on 2013-06-30
> **linuxcenter said:**
> OK How about these rules ?

You're making this much more complicated than it need be.  Stop worrying about blocking ports and block by IP address or interface.

First, you need to put all the rules that allow acceptable traffic ahead of the blocking rules.  Second, it's clear to me that you have a limited understanding of how IP traffic works.  Let's start with this:

> iptables -A OUTPUT -p tcp -m multiport --sports 80,443 -d 0/0 --dports 80,443 -m state --state NEW,ESTABLISHED -j ACCEPT

This will never work because the outbound requests to web servers do not originate from ports 80 and 443 on the client machine.  The client always chooses a random unprivileged port above 1023 for outbound traffic.  Ordinary users cannot bind to a port below 1024; only root can do that.  So clients use high ports for outbound requests.  Also, "-d 0/0" is unnecessary since that is the iptables default.

In any event, if you want to block all incoming traffic to an interface just use:

```
/sbin/iptables -A INPUT -i eth0 -j DROP
```

That blocks everything arriving on the Ethernet interface eth0.

Now as for the OUTPUT rule, is this machine designed to be a firewall router with two interface cards, one pointing to the Internet and one pointing to the LAN?  Or are you trying to block packets leaving the machine itself?  If it is a router with, say, eth0 pointing to the Internet and eth1 pointing inside, use

```

/sbin/iptables -A INPUT -i eth1 -p tcp --dport 80  -j ACCEPT
/sbin/iptables -A INPUT -i eth1 -p tcp --dport 443 -j ACCEPT
/sbin/iptables -A INPUT -i eth1 -j DROP

```

Now people behind the box can reach remote websites but nothing else.

It's a lot easier to specify just the minimal set of rules required to permit what you want to permit then block everything else.

---

### Post by linuxcenter on 2013-07-01
Im on **LAN**, now can i be specific about outgoing rules allow only dport and sport to be 80,443.
If im not hosting a website [B]why do i need ? 

/sbin/iptables -A INPUT -i eth1 -p tcp --dport 80  -j ACCEPT
/sbin/iptables -A INPUT -i eth1 -p tcp --dport 443 -j ACCEPT[/B]

---

### Post by CharlesA on 2013-07-01
As said earlier, your machine communicates with remote servers by picking a random high numbered port. If you wanted to filter traffic, go off the destination port, not both source and destination port. That goes for the Output chain.

As far as the INPUT chain goes, if you aren't hosting any services, it should be fine to drop or reject anything incoming that isn't established or related.

---

### Post by SeijiSensei on 2013-07-01
> **linuxcenter said:**
> Im on **LAN**, now can i be specific about outgoing rules allow only dport and sport to be 80,443.
If im not hosting a website [B]why do i need ? 

/sbin/iptables -A INPUT -i eth1 -p tcp --dport 80  -j ACCEPT
/sbin/iptables -A INPUT -i eth1 -p tcp --dport 443 -j ACCEPT[/B]

If you read my post carefully, you would see that these rules would apply in the situation where your computer sits between a local LAN and the Internet.  In this case all the LAN traffic would be funneled through the box, and the INPUT rules would apply to requests coming from machines behind this computer.

Are you trying to keep *your own computer* from sending packets out to the Internet?  That seems like a bit of paranoia to me, but if you want to do that then use
```

/sbin/iptables -A INPUT -i lo -j ACCEPT
/sbin/iptables -A INPUT -m state --state RELATED,ESTABLISHED -j ACCEPT
/sbin/iptables -A INPUT -j DENY

/sbin/iptables -A OUTPUT -i lo -j ACCEPT
/sbin/iptables -A OUTPUT -p tcp --dport 80  -j ACCEPT
/sbin/iptables -A OUTPUT -p tcp --dport 443 -j ACCEPT
/sbin/iptables -A OUTPUT -j DENY

```

---

