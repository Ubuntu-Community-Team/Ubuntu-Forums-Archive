---
title: "IPTABLES do not work without ROUTE exist ?!"
date: 2009-11-28
forum: Security
---

### Post by kapetr on 2009-11-28
Hello (and sorry please my English),

Maybe it is a bug - and if Yes, then maybe a dangerous one

Problem:
--------
I have connection to my ISP vi DSL modem in bridge mode (direct connection to Internet).

I make it manually by "pppd pty 'pppoe -I eth0' user xx password xx usepeerdns"

the routes:
---------
root@zly-hugo:~# ip route list
88.103.200.47 dev ppp0  proto kernel  scope link  src 90.177.124.235  #GW1
10.0.0.0/24 dev eth0  proto kernel  scope link  src 10.0.0.1 
---------

Before I have defined my default route, I have take note about this:

- in one terminal I run "tcpdump -entvi any"
- in other : "iptables -L -n -v --line-numbers"

And I was aghast.

tcpdump shows attack packets coming in - e.g. telnet TCP-SYN from someone from Internen.

! but - iptables - do not see this packets, packet counters leave unchanged (in all chains).

Only when I bring up my default route, iptables begins to work !!!

I have test this also in double ISP configuration:
--------------------------------------------------

- 2 ISP providers ->
- 2 DSL modems in bridge mode ->
- 2 pppoe links ->
- 2 host routes to GWs

And now is it more complicated:

iptables take notes over attack packet ONLY then, if exist a route to attackers_IP_addres AND this route goes over the same device (e.g. ppp0), through the packet has come in.

For example:

- tcpdump shows intruder packet from Internet comming in over ppp0 (destIP=myIP1 on ppp0) 
- but if my default route is via 2. provider (via GW2/ppp1), then iptables DO NOT process this packet
- but if my default route is via 1. provider (via GW1/ppp0), then iptables works 
 and vice versa.

Interesting, isn't it ?


Any Idea ?

--kapetr

---

### Post by koenn on 2009-11-28
somewhat interesting, yes, but you have to consider  this:

tcpdump will monitor your network interface(s). anything arriving there (even not destined for you) will show up

I assume iptables will only count packets it actually sees/processes. I can imagine how your routing table will have an impact on this, because routing decisions are a factor in iptables' chains and tables. 

So I assume that this behaviour will turn out 'as designed', i.e. not a bug or a security issue. If you want to argue against that, you'll need to set up more specific test scenarios. So you'll have start with describing accurately what your test is supposed to prove or disprove, and then design a test that tests exactly that.

---

### Post by kapetr on 2009-11-29
> **koenn said:**
> somewhat interesting, yes, but you have to consider  this:

tcpdump will monitor your network interface(s). anything arriving there (even not destined for you) will show up

I assume iptables will only count packets it actually sees/processes. I can imagine how your routing table will have an impact on this, because routing decisions are a factor in iptables' chains and tables. 

So I assume that this behaviour will turn out 'as designed', i.e. not a bug or a security issue. If you want to argue against that, you'll need to set up more specific test scenarios. So you'll have start with describing accurately what your test is supposed to prove or disprove, and then design a test that tests exactly that.


- iptables should see/process and especially count packet coming in (INPUT chain) even if there is no route back, or not ?
- these packets are destined for me (their destIP==myIP of (coming in) device 
- even if the "intruder" packets would not really come in (if iptables works, but just do not show it), it should be corrected
- I will try (somehow?)to send packets from outside and I will report, what happens

--kapetr

---

### Post by kapetr on 2009-11-29
I have tested it:

- 2 ppp interfaces and host routes to my 2 ISPs
- and ONLY ONE default route - testing with 

1/ ip route add to default via $GW1
2/ dtto via $GW2

(only one per time)

I have used different online ping services and also one TCP service:

"echo" at  [http://centralops.net/co/](http://centralops.net/co/)  with 
#nc -l -p 7      on my site.

Result:
-------

iptables works exactly as I wrote before:

pings/TCP_echos - are seen/count  by iptables <=> they come in over the device (and to myIP of this device) which is used as default route.
To the other (public) myIP/dev - the packets are seen by tcpdump but not by iptables.

The good note is: these packets (to my other IP - not seen by iptables)  are received, but NOT processed - e.g. no pings replays are send (even if allowed by iptables) and netcat is waiting - not responding to incoming TCP-SYN  packets.


Also - I think, that this behaviour of iptables (not see/count packets coming in without "route back" ) IS A BUG, but fortunately NOT DANGEROUS.

I hope, my tests were good enough.


--kapetr

---

### Post by The Cog on 2009-11-29
I wonder if the packets are being dropped by the kernel before iptables ever sees them, because of the lack of a return route. it would be interesting to try the test again with reverse path filtering disabled. Try this:
> sudo -i
echo 0 > /proc/sys/net/ipv4/conf/ppp0/rp_filter
exitand then run your tests again.

Reverse path filtering drops packets which come in on an interface that doesn't hold the route to the packets source address. It is really intended to counter address spoofing, but if you don't have a default route then packets sent from most IP addresses would be dropped. 

I'm not certain that rp_filter is the explanation, so the test results would be interesting.

---

### Post by koenn on 2009-11-29
> **The Cog said:**
> I wonder if the packets are being dropped by the kernel before iptables ever sees them, because of the lack of a return route. 
I was thinking something along those lines as well, but since I only have one internet connection, I'd probably have to do something elaborate with multiple VM's and virtual networks to get a decent test environment, and I'm not in the mood for it.

---

### Post by __p1n__ on 2009-11-29
> **The Cog said:**
> I wonder if the packets are being dropped by the kernel before iptables ever sees them

The first netfilter hook is in ip_input.c:ip_rcv() however you will need to have a PRE-chain iptables rule defined to use it.  If the packet can't be delivered or forwarded then it will be dropped without further processing.

edit: to clarify, a packet needs to be successfully received before any PRE-chain netfilter rules are applied.

---

### Post by __p1n__ on 2009-11-30
> **kapetr said:**
> ... Also - I think, that this behaviour of iptables (not see/count packets coming in without "route back" ) IS A BUG, but fortunately NOT DANGEROUS.

I hope, my tests were good enough.

--kapetr

There's no bug at all; simply a lack of knowledge on your part with respect to linux networking and iptables/netfilter.  The "attack" packets that you see with tcpdump are dropped by the packet handler if they're malformed or not routable.  You can create a PRE-ROUTING chain rule to get some visibility of the packets falling into the latter category if you really want to see them.  You're not going to see anything in the INPUT chain until the packet makes it to local delivery.

Netfilter/iptables is not designed to be an IDS but rather a set of routing filters so if you want a tool that is a network IDS then use snort or something similar.

---

### Post by kapetr on 2009-12-01
**for #5 - The Cog**

- I have tested it (in my dual Internet-link config. with default route only ower $GW1/ppp0)
- after 
> 
echo 0 > /proc/sys/net/ipv4/conf/ppp0/rp_filter
echo 0 > /proc/sys/net/ipv4/conf/ppp1/rp_filter
 

nothing has changed - incoming packets (over ppp1 to my $IP2) are seen by "tcpdump -entvi ppp1" but not by IPTABLES - INPUT

? with Yours explanation of /proc/sys/net/ipv4/conf/ppp0/rp_filter I would expect, that now should these packet be seen by iptables

**for #8 - __p1n__**
> 
You're not going to see anything in the INPUT chain until the packet makes it to local delivery.

As I wrote: these packets are for me - their destIP == myIP2 (of my site of ppp1)

And about the "PRE-ROUTING chain" - I will try it, but today is last day, when I have these 2 ADSL connections 

- I have tested it:

> Chain PREROUTING (policy ACCEPT 7 packets, 372 bytes)
num   pkts bytes target     prot opt in     out     source               destination         
1        4   192            all  --  ppp1   *       0.0.0.0/0            0.0.0.0/0           
2        3   180            all  --  ppp0   *       0.0.0.0/0            0.0.0.0/0           

Chain POSTROUTING (policy ACCEPT 55 packets, 3390 bytes)
num   pkts bytes target     prot opt in     out     source               destination         

Chain OUTPUT (policy ACCEPT 55 packets, 3390 bytes)
num   pkts bytes target     prot opt in     out     source               destination         

-> and really - these packets are seen in this table/chain

But - what I'm surprised - on ppp0 (using to normal routing) I do not see all packets - e.g. I reload one web page in browser, in standard INPUT chain are added e.g. +- 200 packets, put in PREROUTING on ppp0 just +- 4 ?

As would not go all packets over PREROUTING chain ? 

> The "attack" packets that you see with tcpdump are dropped by the packet handler if they're malformed or not routable.

BTW - _why are these packets no routable ?_ Their  dstIP is OK (mine) and to their srcIP route exist - just over another interface. And - as I have tested (without "ip rule add src ..." rules) - it was nothing special, that packets has go out over wrong interface.  


--kapetr

---

### Post by koenn on 2009-12-01
> **kapetr said:**
> [B]
nothing has changed - incoming packets (over ppp1 to my $IP2) are seen by "tcpdump -entvi ppp1" but not by IPTABLES - INPUT

...

As I wrote: these packets are for me - theyr destIP == myIP2 (of my site of ppp1)


simplified diagram from 
[http://www.netfilter.org/documentation/HOWTO//packet-filtering-HOWTO-6.html](http://www.netfilter.org/documentation/HOWTO//packet-filtering-HOWTO-6.html)
```

                          _____
Incoming                 /     \         Outgoing
       -->[Routing ]--->|FORWARD|------->
          [Decision]     \_____/        ^
               |                        |
               v                       ____
              ___                     /    \
             /   \                  |OUTPUT|
            |INPUT|                  \____/
             \___/                      ^
               |                        |
                ----> Local Process ----


```
note that PRE-ROUTING and POST-ROUTING are left out, 
it's merely meant as an indication that what arrives at your NIC ("Incoming") does not necessarily have to show up in "INPUT" (or "FORWARD").
You'd have to have a rather detailed understanding of how your NIC and its kernel modules, your TCP/IP stack, and the netfilter components, interact with each other - there's a lot more to it than 'it has my IP address in its dest field, so I have to see it".


edit: have a look here [http://www.frozentux.net/iptables-tutorial/chunkyhtml/c962.html](http://www.frozentux.net/iptables-tutorial/chunkyhtml/c962.html) for a more detailed diagram.

---

### Post by kapetr on 2009-12-01
> ...there's a lot more to it than 'it has my IP address in its dest field, so I have to see it".

Can You giv please to me some links, where I can find more detailed info ?

I can't uderstand, why packet, which:
- comes to my interface with my MAC_address (of this interface) as target
- has my IP adress as targed 

could not to be for me and processed by my INPUT chain ?

And sa I wrote, should not all packets be processed by "-t nat PREROUTING" chain ?

--kapetr

---

### Post by __p1n__ on 2009-12-01
> **kapetr said:**
> Can You giv please to me some links, where I can find more detailed info ?

I can't uderstand, why packet, which:
- comes to my interface with my MAC_address (of this interface) as target
- has my IP adress as targed 

could not to be for me and processed by my INPUT chain ?

And sa I wrote, should not all packets be processed by "-t nat PREROUTING" chain ?

--kapetr


As mentioned a packet has to be properly received before it hits the PRE-ROUTING chain netfilter hook.  INPUT doesn't mean what you are assuming it means in the generic sense but rather some specific in regards to local delivery.

Since you seem sincerely interested in this you should consult the source.

Download the following: [http://ftp.de.debian.org/debian/pool/main/l/linux-2.6/linux-2.6_2.6.30.orig.tar.gz](http://ftp.de.debian.org/debian/pool/main/l/linux-2.6/linux-2.6_2.6.30.orig.tar.gz) and look at the ip_input.c file.  The relevant function is called ip_rcv() and you can follow the logic and note all the points where a packet can be dropped before the PRE-ROUTING netfilter function is called (literally at the return from the ip_rcv() function.)

You can also see where the INPUT and FORWARD netfilter hooks are.

All of your questions are answered by consulting the source.

---

### Post by The Cog on 2009-12-01
I still think it's probably due to the reverse path filtering that they don't show up in the iptables log. I am guessing that my instructions for disabling rp_filter were inadequate. When I get time, I'll try it myself but that won't be for a day or two.

---

### Post by The Cog on 2009-12-01
Yup. I confirm a few things by experiment:

Firstly, removing the default route does indeed stop the iptables INPUT chain from logging incoming packets from unknown sources.

Secondly, the -t nat -A PREROUTING chain continues to log them. This says to me that they are being dropped by the routing process.

Thirdly, 
echo 0 > /proc/sys/net/ipv4/conf/wlan0/rp_filter
echo 0 > /proc/sys/net/ipv4/conf/all/rp_filter
starts the INPUT chain logging them again.

Fourthly, 
echo 0 > /proc/sys/net/ipv4/conf/wlan0/rp_filter
echo 0 > /proc/sys/net/ipv4/conf/all/rp_filter
doesn't stop the INPUT chain from logging them again. I don't understand why not.

---

### Post by koenn on 2009-12-01
> **kapetr said:**
> Can You giv please to me some links, where I can find more detailed info ?

I can't uderstand, why packet, which:
- comes to my interface with my MAC_address (of this interface) as target
- has my IP adress as targed 

could not to be for me and processed by my INPUT chain ?

And sa I wrote, should not all packets be processed by "-t nat PREROUTING" chain ?

--kapetr
what __p1n__ said. 

to add my own perspective (I'm not a programmer and I don't read code a lot)
 - an IP packet does not know about MAC addresses. MAC adresses belong to the Datalink layer, IP has no knowledge of those. You should read about how network protocols are stacked into a layered suites, eg start here [http://en.wikipedia.org/wiki/Internet_Protocol_Suite](http://en.wikipedia.org/wiki/Internet_Protocol_Suite) and follow the links

- is is obvious from the diagram i posted earlier, and the source  __p1n__ refered to, that between your NIC (and its device driver ) and iptables, there will be quite a bit of processing. For starters, the kernel will need to decide whether the packet has to go to iptables INPUT, or to FORWARD. It does also a number of sanity checks first. The rp_filter The Cog refers to is one of them. There are others, eg [http://www.linuxdocs.org/HOWTOs/Adv-Routing-HOWTO-12.html](http://www.linuxdocs.org/HOWTOs/Adv-Routing-HOWTO-12.html)
TThen, in some cases (eg NAT), the destination address of the packet may be modified. 

Only if a packet gets though all that, and still has your machine's IP address as destination,  iptables INPUT will see that packet.

As for PREROUTING, maybe not all packets pass through it because the prerouting, especially in the nat table, needs to decide whether the src or dst address of a packet needs to be changed. possiblly, this decision needs to be taken only once for all packets in the same stream, because the decision will be the same for all packets. That might explain why the count here is lower - and I admit i'm speculating a bit here.
But if you want to be sure, you'll probably find it in some advanced iptables documentation (or the source code). Before you go there, it's probably best to learn the basics.

---

### Post by koenn on 2009-12-01
> **The Cog said:**
> 
Thirdly, 
echo 0 > /proc/sys/net/ipv4/conf/wlan0/rp_filter
echo 0 > /proc/sys/net/ipv4/conf/all/rp_filter
starts the INPUT chain logging them again.

Fourthly, 
echo 0 > /proc/sys/net/ipv4/conf/wlan0/rp_filter
echo 0 > /proc/sys/net/ipv4/conf/all/rp_filter
doesn't stop the INPUT chain from logging them again. I don't understand why not.

hm, unless I'm missing something, 
if you echo 0 to turn the rp_filter of, shouldn't you echo something >0 to turn them on again ?


edit:
[http://www.linuxdocs.org/HOWTOs/Adv-Routing-HOWTO-12.html](http://www.linuxdocs.org/HOWTOs/Adv-Routing-HOWTO-12.html)
> 
The following fragment will turn this on for all current and future interfaces.
```

    # for i in /proc/sys/net/ipv4/conf/*/rp_filter ; do
    >  echo 2 > $i 
    > done

```


---

### Post by The Cog on 2009-12-01
> **koenn said:**
> hm, unless I'm missing something, 
if you echo 0 to turn the rp_filter of, shouldn't you echo something >0 to turn them on again ?
Doh! Typing error - I used 1 to turn them back on again.> 

edit:
[http://www.linuxdocs.org/HOWTOs/Adv-Routing-HOWTO-12.html](http://www.linuxdocs.org/HOWTOs/Adv-Routing-HOWTO-12.html)
Nice link. Doesn't explain why I might want to set it to 2 though. The default (in ubuntu) is 1, and 0 seems to turn it off. I can't find any other references to setting it to 2, other than copy/paste copies of the page linked above. I wonder if it's a typo that's been propogated around.

---

### Post by koenn on 2009-12-02
> **The Cog said:**
> 
Nice link. Doesn't explain why I might want to set it to 2 though. The default (in ubuntu) is 1, and 0 seems to turn it off. I can't find any other references to setting it to 2, other than copy/paste copies of the page linked above. I wonder if it's a typo that's been propogated around.
Yeah, it looked weird to me, too. I always thought these things were flags you turn on or off, so 0 or 1.

---

