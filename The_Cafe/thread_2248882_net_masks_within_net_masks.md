---
title: "net masks within net masks?"
date: 2014-10-17
forum: The Cafe
---

### Post by haplorrhine on 2014-10-17
If a more inclusive net mask shares its leading bits with a less inclusive net mask, would the former include all of the addresses of the latter?

My understanding is that each IPv4 address is a series of 4 8-bit octets, and a net mask is an address followed by /n where n is an integer indicating that the included addresses are the addresses for which the first n bits are shared with the net mask address.
This system doesn't sound awfully specific.  How are these system used typically?  How do they ensure that no other networks will have an address that falls within a netmask?

added:  As far as iptables rules go, could I just use stars (*) instead of a net mask?

---

### Post by TheFu on 2014-10-18
The netmask tells equipment which things are "local" to the LAN and should be reached using ethernet (run arp).  IP is needed to reach systems outside the netmask.  The netmask is handy for routing, so changing it without understanding that will likely break the routing.

A network engineer would setup the devices so there aren't any conflicts for subnets on a corporate network. When a mistake happens, entire subnets get dropped and lots of people complain quickly.

Security Now! - a podcast did a "how the internet works" series of episodes a few years ago. The description was accurate and I was able to picture everything based on verbal descriptions provided.  Plus they have human-created transcripts.  Look for episode 25 - at grc.com/sn

---

### Post by Doug S on 2014-10-18
> **haplorrhine said:**
> added:  As far as iptables rules go, could I just use stars (*) instead of a net mask?To specify any IP address use 0.0.0.0/0.

 To specify an exact IP address don't specify any mask, or specify 32. Examples: 192.168.17.13/32 or 192.168.17.13

To specify a range of, say 8, IP addresses use 29, typically with the base address. Example. 192.168.17.8/29

And so on.

You can not use "*". You will get this error:```
iptables v1.4.12: invalid mask `*' specified
```

---

### Post by The Cog on 2014-10-18
The mask is just the slash and following number, so in 1.2.3.4/24 the mask is /24. 
The mask indicates how much of the IP address should be regarded as the network number, and how much should be regarded as just identifying a host on that network.
In the example above, the network is 24 bits It is normal when talking about network numbers to use all 0 bits for the host part of the address, so the network part is 1.2.3 and the network number is 1.2.3.0. IP addresses that live within that network (1.2.3.0-1.2.3.255) can all talk directly to each other without needing to talk via a router. Hosts wanting to talk to other hosts that are **not** on the same network must send their messages to a router that is connected to their network, and the router will pass them on.
> How do they ensure that no other networks will have an address that falls within a netmask?
Hope this example helps:
Imagine an office block that has no more than 200 PCs on each floor. They might decide to give each floor its own network number, e.g. 10.0.1.0/24, 10.0.2.0/24, 10.0.3.0/24 etc. Then PCs on each floor can talk directly to each other, and use a router when they talk between floors.

Giving a host the right address but the wrong mask is a mistake. For instance in the example above, configuring a PC as 10.0.4.19/16 in the above example would leave it thinking it should be able to talk directly to any other PC starting with 10.0, so it would not be able to talk to PCs on other floors because it wouldn't think it needed to talk via a router. It would try to talk directly and get no answer.

But the company has many buildings. They may decide to advertise the entire building to the rest of the company network as 10.0.0.0/16 (net 10.0 and hosts 0.0-255.255). Externally the building looks like a single 16-bit network, but when messages get to the building, the routers in the building use the /24 subdivsion to route to the appropriate floor. In this case, networks falling within other larger networks is actually the norm and it is called summarising. It needs to be thought out carefully or some parts may not be reachable from some other parts. 

I don't think you can use * in iptables - you have to use a proper mask which says exactly how many bits to check and how many to ignore.

You may sometimes see a mask written in dotted quad notation, e.g. 255.255.255.0. This form gives a 32-bit value that consists of n 1s followed by 32-n zeros. 255.255.255.0 has 24 leading ones, and so means the same as /24.

People tend to prefer /8, /16 and /24 masks because the network/host boundary falls on a byte boundary and it's easy to read the network part. Something like 11.22.33.44/28 implies network 11.22.33.32 containing addresses 11.22.33.32-11.22.33.47 and that kind of thinking does my head in. Ugh.

---

### Post by Doug S on 2014-10-18
> **The Cog said:**
> You may sometimes see a mask written in dotted quad notation, e.g. 255.255.255.0. This form gives a 32-bit value that consists of n 1s followed by 32-n zeros. 255.255.255.0 has 24 leading ones, and so means the same as /24.I had forgotten about the dotted quad notation. While I can not think of a reason why it would be needed, it does provide a way to have whatever bit mask one wants. Example:```
# . check the static blacklist.
#
# http related
$IPTABLES -A http-new-in -i $EXTIF -s 5.100.113.117/255.255.0.255 -j DROP
$IPTABLES -A http-new-in -i $EXTIF -s 5.100.113.117/255.255.255.0 -j DROP
$IPTABLES -A http-new-in -i $EXTIF -s 5.248.83.0/24 -j DROP
```Which gives (from "sudo iptables -v -x -n -L | more"):```
Chain http-new-in (1 references)
    pkts      bytes target     prot opt in     out     source               destination
       0        0 DROP       all  --  eth1   *       5.100.0.117/255.255.0.255  0.0.0.0/0
       0        0 DROP       all  --  eth1   *       5.100.113.0/24       0.0.0.0/0
       0        0 DROP       all  --  eth1   *       5.248.83.0/24        0.0.0.0/0
```

---

### Post by The Cog on 2014-10-18
> **Doug S said:**
> I had forgotten about the dotted quad notation. While I can not think of a reason why it would be needed, it does provide a way to have whatever bit mask one wants. Example:```
# . check the static blacklist.
#
# http related
$IPTABLES -A http-new-in -i $EXTIF -s 5.100.113.117/255.255.0.255 -j DROP
$IPTABLES -A http-new-in -i $EXTIF -s 5.100.113.117/255.255.255.0 -j DROP
$IPTABLES -A http-new-in -i $EXTIF -s 5.248.83.0/24 -j DROP
```Which gives (from "sudo iptables -v -x -n -L | more"):```
Chain http-new-in (1 references)
    pkts      bytes target     prot opt in     out     source               destination
       0        0 DROP       all  --  eth1   *       5.100.0.117/255.255.0.255  0.0.0.0/0
       0        0 DROP       all  --  eth1   *       5.100.113.0/24       0.0.0.0/0
       0        0 DROP       all  --  eth1   *       5.248.83.0/24        0.0.0.0/0
```

You are right of course. It's unusual to want complicated filter rules like that, but perfectly feasible. 

I believe that use of dis-contiguous masks, ones that are not just ones followed by zeros, is not allowed in routing - you cannot configure such network/masks in a routed network. I don't think routers these days would accept it.

---

### Post by haplorrhine on 2014-10-18
This really helps.

Now I'm getting into Ubuntu help, but I'm guessing that I only must distinguish the "from" addresses in ufw since the "to" will always be the same unless I do something funky with my configuration?

Also a question about the C* network in Table A-4 of the link.  [http://www.cisco.com/en/US/docs/security/vpn5000/manager/reference/guide/appA.html](http://www.cisco.com/en/US/docs/security/vpn5000/manager/reference/guide/appA.html)
THe last octect of the network is 64, which is 01000000, so shouldn't the subnetwork address end in 192, 11000000, rather than 224, 11100000?  Or can the network portion end with a zero (e.g. 198.41.9.64/32 as opposed to /64)?

> **The Cog said:**
> 
I don't think you can use * in iptables - you have to use a proper mask  which says exactly how many bits to check and how many to ignore.

You may sometimes see a mask written in dotted quad notation, e.g.  255.255.255.0. This form gives a 32-bit value that consists of n 1s  followed by 32-n zeros. 255.255.255.0 has 24 leading ones, and so means  the same as /24.

People tend to prefer /8, /16 and /24 masks because the network/host  boundary falls on a byte boundary and it's easy to read the network  part. Something like 11.22.33.44/28 implies network 11.22.33.32  containing addresses 11.22.33.32-11.22.33.47 and that kind of thinking  does my head in. Ugh.

It seems the forum's uploader automatically shrank my 250x250 tarsier avatar to 90x90, so I left it.

I just learned how the binary strings correspond to the Latin  numbers of the IP address, which I explain for anybody interested.
When counting with Latin numbers, you proceed  through all ten digits before increasing the next right-most digit by  one.  Well, when converting the binary code into Latin numbers, they treat  the binary as a two-digit system of counting.  Thus, as you proceed through  all possible octet values, of which there are 256 ( 2[SUP]^8 [/SUP]),  the left-most value changes only once at halfway, at 127/128.  Therefore, conventiently, having the octet above or below 127½ corresponds to one or the other subnetwork, respectively.  See Table A-3 in the link.  [http://www.cisco.com/en/US/docs/security/vpn5000/manager/reference/guide/appA.html](http://www.cisco.com/en/US/docs/security/vpn5000/manager/reference/guide/appA.html)
Note that the subnetwork upper limits are 2^7-1 (127) and 2^8-1 (255) because we started counting at zero.

---

### Post by mips on 2014-10-21
> **The Cog said:**
> 
I believe that use of dis-contiguous masks, **ones that are not just ones followed by zeros**, is not allowed in routing - you cannot configure such network/masks in a routed network. I don't think routers these days would accept it.

You are correct that routers have very strict rules wrt subnet masks but they don't have to be followed by zeros, /30 or 255.255.255.252 for exmple is fine and commonly used for point-to-point serial or data links as it provides a ip address for each of the two endpoints/interfaces as well as a network & broadcast addrress, wasting nothing.

In the old days you only had clasful routing where you could not do the above and had to route on strict class a, b, c boundaries. This was highly inefficient use of address space until classless routing came along allowing above and other nice things like variable length subnet masking (VLSM) etc

---

### Post by haplorrhine on 2014-10-21
but 255.255.255.252 _*is*_ followed by zeros.
11111111.11111111.11111111.11111100

30 is odd though.
.00011110
What does that mean?  That I can change the first four of the last five bits?  Could I end that net address with a 161?

---

### Post by TheFu on 2014-10-21
I found using a network calculater to get a feel for these things was extremely helpful.  My ISP give me a /29, for example.  A long time ago, it was easy to get a /28 from ISPs without being hassled too much.

IPv6 solves the subnet restrictions for everyone.  When available, I expect my ISP will give us /54 or /48 subnets on IPv6 - larger than the entire internet addr space today.

---

### Post by The Cog on 2014-10-21
> **haplorrhine said:**
> but 255.255.255.252 _*is*_ followed by zeros.
11111111.11111111.11111111.11111100

Spot on. It is 30 1s followed by 2 0s.
> 
30 is odd though.
.00011110
What does that mean?  That I can change the first four of the last five bits?  Could I end that net address with a 161?
No, the mask when written as "/30" means  that the network part of the address is 30 ones long. 30 ones (followed by 2 zeros to make up 32 bits) gives the mask above. 
/30 means 255.255.255.252 means 11111111.11111111.11111111.11111100
That mask means it can only contain 4 addresses. Given that 00 (the network number) and 11 (the broadcast address) are usually reserved, it leaves space for two addresses which is just right for a point-to-point network link.

You always fill the host part of the address with 0s when talking about the network number.
10.22.33.44/28 means the last byte is chopped in half. The network number is 10.22.33.32 and the addresses on that network are 10.22.33.32 - 10.212.33.63. 10.22.33.44 is just one of the hosts on the network.

---

### Post by haplorrhine on 2014-10-21
I think I'm starting to confuse concepts.  Thank you.  You are right.

---

### Post by mips on 2014-10-21
> **The Cog said:**
> Spot on. It is 30 1s followed by 2 0s.


I was not working in binary, was more referring to masks or networks not having the last octet as zero. Apologies for the confusion.

---

### Post by mips on 2014-10-21
[http://www.unixwiz.net/techtips/netmask-ref.html](http://www.unixwiz.net/techtips/netmask-ref.html)

[IMG]http://s27.postimg.org/snk461obn/netmask.png[/IMG]

Beyond this you can VLSM creating smaller or bigger masks for the different class networks.

---

### Post by haplorrhine on 2014-10-21
It's just powers of two, man.

where n = number of bits free
Latin octet equals 255 subtracted by &#931;[SUP]n-1[/SUP][SUB]k=0[/SUB](2[SUP]k[/SUP])

---

### Post by haplorrhine on 2014-10-21
I didn't mean to discourage you from posting, **mips**.  I appreciate your input.

This just occurred to me.  In our Latin system, each shift to the left reflects a change by a power of ten.  In the binary, similarly, each shift to the left is a power of 2 change.  Therefore, we could memorize all the corresponding values for smaller chunks, like a triplets, and multiply for each chunk.
000 = 0
001 = 1
010 = 2
011 = 3
100 = 4
101 = 5
110 = 6
111 = 8
three spaces = 2^3 = 8

Then if you see, for example, 11101010, split it into 11, 101, 010
11 = 3 x 64 = 192
101 = 5 x 8 = 40
010 = 2 x 1 = 2
adds up to 234

You could also switch the zeros and ones and subtract from 255.
11101010 -> 00010101
010 = 2 x 8 = 16
101 = 5
255 - 21 = 234

---

### Post by The Cog on 2014-10-22
Just nit-picking a typing error:  111=7 (not 111=8).

Ew! I have never felt the urge to work in tri-bits. 
> Latin octet equals 255 subtracted by &#931;[SUP]n-1[/SUP][SUB]k=0[/SUB](2[SUP]k[/SUP])
Er - if you say so. :)

---

### Post by haplorrhine on 2014-10-24
Wouldn't the system be easier as digits representing triplets?  They would still be three-digit numbers since the triplet only goes up to seven.

---

### Post by The Cog on 2014-10-27
You mean so the mask was e.g. 377.377.377.0? Using octal instead of decimal for each octet? I'm not sure. It's easier to convert 377.377.377.360 to binary than 255.255.255.240 I guess. And I would think the people who chose to standardise on decimal would have been familiar with octal - the switches on a PDP are coloured in groups of 3 for easy entry of octal values. But they chose decimal. Maybe they didn't anticipate splitting bytes. The original system only used class A (/8), B (/16) or C (/24) addresses so the masks only ever contained the numbers 255 and 0. Splitting masks on other boundaries didn't happen till much later when address space started running short, something that was inconceivable for quite a while.

---

### Post by mips on 2014-10-27
> **haplorrhine said:**
> Wouldn't the system be easier as digits representing triplets?  They would still be three-digit numbers since the triplet only goes up to seven.

Just work in binary, a base two system is very simple to understand and work with.

---

