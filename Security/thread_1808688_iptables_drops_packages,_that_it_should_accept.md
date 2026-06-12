---
title: "iptables drops packages, that it should accept"
date: 2011-07-20
forum: Security
---

### Post by SpinningAround on 2011-07-20
For some reason do iptables drop these packages and I don't understand why. The log output rule, is at the very end so these packages manage to get pass rules that should accept them.

What I can see is the IP ok (0.0.0.0/0), the source ports are fine since outgoing port (local) don't fall within the port "hole", so why doesn’t iptables accept the package?

```

OUT DROPPED: IN= OUT=tap0 SRC=258.589.123.145 DST=123.456.789.12 LEN=52 TOS=0x00 PREC=0x00 TTL=64 ID=30604 DF PROTO=TCP SPT=39287 DPT=80 WINDOW=123 RES=0x00 ACK PSH FIN URGP=0

```

```

ACCEPT     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           tcp spts:1024:19273 state NEW,ESTABLISHED 
ACCEPT     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           tcp spts:21580:65535 state NEW,ESTABLISHED 

```

[PHP]
iptables -A OUTPUT -p tcp --sport 1024:$((PORT_OUT_BEGIN - 1)) -m state --state NEW,ESTABLISHED -j ACCEPT
iptables -A OUTPUT -p tcp --sport $((PORT_OUT_END + 1)):65535 -m state --state NEW,ESTABLISHED -j ACCEPT
[/PHP]

---

### Post by bodhi.zazen on 2011-07-20
You will need to post a lot more information then that.

First, with iptables, the order of rules is critical, so you can not -A a rule and expect the packet to be accepted if an earlier rule drops the packet.

Second, you are using a tap, so your networking is going to be more complex and your problem may be in your forwarding chain ;)

---

### Post by SpinningAround on 2011-07-21
Here is the rules, there might be things I overlooked since I haven't used iptables before.

**Input rules**
```

Chain INPUT (policy DROP 0 packets, 0 bytes)
 pkts bytes target     prot opt in     out     source               destination         
    0     0 ACCEPT     udp  --  *      *       0.0.0.0/0            0.0.0.0/0           udp spt:53 dpts:1024:23456 state ESTABLISHED 
    0     0 ACCEPT     udp  --  *      *       0.0.0.0/0            0.0.0.0/0           udp spt:53 dpts:23478:65535 state ESTABLISHED 
 
    0     0 ACCEPT     udp  --  *      *       0.0.0.0/0            0.0.0.0/0           udp spt:123 dpts:1024:23456 state ESTABLISHED 
    0     0 ACCEPT     udp  --  *      *       0.0.0.0/0            0.0.0.0/0           udp spt:123 dpts:23478:65535 state ESTABLISHED 
 
    0     0 LOG        icmp --  *      *       0.0.0.0/0            0.0.0.0/0           icmp type 0 state RELATED,ESTABLISHED limit: avg 1/min burst 1 LOG flags 0 level 4 prefix `PINGED: ' 
    0     0 ACCEPT     icmp --  *      *       0.0.0.0/0            0.0.0.0/0           icmp type 0 state RELATED,ESTABLISHED 

    0     0 ACCEPT     tcp  --  *      *       178.73.215.160/28    0.0.0.0/0           tcp spts:1194:1201 state RELATED,ESTABLISHED 
    0     0 ACCEPT     udp  --  *      *       178.73.215.160/28    0.0.0.0/0           udp spts:1194:1201 state RELATED,ESTABLISHED 

    0     0 ACCEPT     tcp  --  tap0   *       0.0.0.0/0            188.126.74.0/23     tcp dpts:23457:23477 state NEW,ESTABLISHED 
    0     0 ACCEPT     tcp  --  tap0   *       0.0.0.0/0            178.73.196.0/23     tcp dpts:23457:23477 state NEW,ESTABLISHED 

    0     0 LOG        all  --  eth0   *       127.0.0.1            0.0.0.0/0           limit: avg 2/sec burst 5 LOG flags 0 level 7 prefix `FALSE LO: ' 
    0     0 DROP       all  --  eth0   *       127.0.0.1            0.0.0.0/0           

    0     0 ACCEPT     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           tcp dpts:1024:23456 state ESTABLISHED 
    0     0 ACCEPT     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           tcp dpts:23478:65535 state ESTABLISHED 
    0     0 ACCEPT     all  --  lo     *       0.0.0.0/0            0.0.0.0/0           
    0     0 LOG        tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           limit: avg 10/min burst 15 LOG flags 0 level 4 prefix `IN DROPPED: ' 

```

**Output rules**
```

Chain OUTPUT (policy DROP 0 packets, 0 bytes)
 pkts bytes target     prot opt in     out     source               destination         
    0     0 ACCEPT     udp  --  *      *       0.0.0.0/0            0.0.0.0/0           udp spts:1024:12345 dpt:53 state NEW,ESTABLISHED 
    0     0 ACCEPT     udp  --  *      *       0.0.0.0/0            0.0.0.0/0           udp spts:12367:65535 dpt:53 state NEW,ESTABLISHED 

    0     0 ACCEPT     udp  --  *      *       0.0.0.0/0            0.0.0.0/0           udp spts:1024:12345 dpt:123 state NEW,ESTABLISHED 
    0     0 ACCEPT     udp  --  *      *       0.0.0.0/0            0.0.0.0/0           udp spts:12367:65535 dpt:123 state NEW,ESTABLISHED 

    0     0 ACCEPT     tcp  --  *      tap0    188.126.74.0/23      0.0.0.0/0           tcp spts:12346:12366 state NEW,ESTABLISHED 
    0     0 ACCEPT     tcp  --  *      tap0    178.73.196.0/23      0.0.0.0/0           tcp spts:12346:12366 state NEW,ESTABLISHED 

    0     0 ACCEPT     tcp  --  *      *       0.0.0.0/0            178.73.215.160/28   tcp dpts:1194:1201 state NEW,RELATED,ESTABLISHED 
    0     0 ACCEPT     udp  --  *      *       0.0.0.0/0            178.73.215.160/28   udp dpts:1194:1201 state NEW,RELATED,ESTABLISHED 

    0     0 ACCEPT     icmp --  *      *       0.0.0.0/0            178.73.215.160/28   icmp type 3 state NEW,RELATED,ESTABLISHED 

    0     0 ACCEPT     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           tcp spts:1024:12345 state NEW,ESTABLISHED 
    0     0 ACCEPT     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           tcp spts:12367:65535 state NEW,ESTABLISHED 
    0     0 ACCEPT     all  --  *      lo      0.0.0.0/0            0.0.0.0/0           
    0     0 LOG        all  --  *      *       0.0.0.0/0            0.0.0.0/0           limit: avg 10/min burst 15 LOG flags 0 level 4 prefix `OUT DROPPED: ' 

```

packages that get dropped but shouldn’t 
```

OUT DROPPED: IN= OUT=tap0 SRC=188.126.74.1 DST=*.*.*.* LEN=120 TOS=0x00 PREC=0x00 TTL=64 ID=33858 DF PROTO=TCP SPT=12356 DPT=14349 WINDOW=123 RES=0x00 ACK PSH FIN URGP=0
IN DROPPED: IN=tap0 OUT= SRC=*.*.*.* DST=188.126.74.1 LEN=40 TOS=0x00 PREC=0x00 TTL=118 ID=21228 DF PROTO=TCP SPT=2480 DPT=23467 WINDOW=17368 RES=0x00 ACK FIN URGP=0 

```

---

### Post by The Cog on 2011-07-21
Both the packets you show being dropped are FIN packets. I wonder if perhaps FIN (disconnect request) packets are not regarded as NEW,ESTABLISHED. Try adding RELATED to the list, or better still add it as a separate line so you can see counters against that line separately.

Does the connection work up until the point where you try to disconnect again?

Come to think of it, the rules you posted show 0 counters for everything. If this isn't because you just reset iptables, then maybe there is a completely different problem to my diagnosis.

---

### Post by bodhi.zazen on 2011-07-21
In general ...

1. I do not use state (new,related,established) with udp or icmp.

2. Rules for NEW tend to go together, here you define incoming traffic to your services.

3. Rules for RELATED,ESTABLISHED go together, without designating a port. Here you define incoming traffic to your clients.

4. Usually the rules for your tap go in forwarding (rather then input / output), well at least for my setup where the tap is usually a virtual machine.

My guess is your dropped packets have to do with forwarding as I do not see a DROP in your input or output rules, meaning they are dropped by policy, meaning they did not match your accept rules.

See : [http://www.revsys.com/writings/quicktips/nat.html](http://www.revsys.com/writings/quicktips/nat.html)

You will have to modify those rules ( s/eth1/tap0 ;) )

Once you get your rules up, you can further shape them by specifying your incoming client traffic and restricting it to the higher ports, but, if you have incoming traffic to clients on the lower ports, you need more then iptables ;)

---

### Post by The Cog on 2011-07-21
1:
Agreed. It is usual to have a rule that allows RELATED,ESTABLISHED with no other conditions - this rule then allows the continuation of connections that were allowed to get started by other rules (such as new tcp/udp connections on selected ports). I believe that ESTABLISHED does work on both udp and icmp, otherwise a default deny inbound would prevent ping and dns from working.

2, 3: Yup.


I just did a test, and it looks like FIN packets are indeed treated as ESTABLISHED. So forget what I said about adding RELATED. But if occurs to me that retransmitted FIN packets due to packet loss might be dropped because conntrack thinks the connection is already closed. So I wonder why he is posting the question - does he have actual problems, or is he just worrying about occasional log messages reporting dropped packets.

---

### Post by SpinningAround on 2011-07-22
Thanks for all the help and all advice :)

---

