---
title: "2 NIC setup: for any networking gurus out there"
date: 2005-08-03
forum: Server Platforms
---

### Post by adeh on 2005-08-03
Hello,

I am not quite a linux newbie, but I can not consider myself an expert. I have posted about this problem before, but I thought that it was a hardware failure at the router level. Now, I am convinced that something is wrong in my configuration, and I just don't understand it well enough to know what is wrong.

The sitation is: I have a web server, running Ubuntu, in the IT office for remote offices to connect to. It sits in a DMZ behind a Netgear ADSL router (firewall builtin, NAT configured). The server has a second NIC that is connected to the switch for  the internal company LAN, so that the webapps have access to the DB server (running windows). The majority of network traffic flows through a second computer attached directly to the router, running the MS ISA firewall (not my fault).

The problem is that although it seems to work a majority of the time, every once in a while, maybe 5-10 times a day, remote connections to the web server timeout. This lasts for about 10-20 min, then without modifying any config, the connection comes right back. *Sometimes* resetting the router will bring back the connection immediately. Always, restarting the web-server also brings back the connection. As far as I can tell (I have been running this for about 9 months) there is no pattern at all to the service breakdown. Some days it works beautifully, some days it is like pulling teeth.

My question is twofold. 
1. Is there a better setup? A more secure and easy way to connect my web server (subnet 192.16.0.0) to my db server (subnet 192.168.1.0). I have already failed at trying to put the web-server behind the ISA server (and hence on the same subnet as the Db server), due to constraints beyond my control

2. If what I have done is reasonable, what is wrong? Here I post my /etc/network/interfaces

# The loopback network interface
auto lo
iface lo inet loopback

# The outward network interface
auto eth1
iface eth1 inet static
name out-facing LAN card
broadcast 192.168.0.255
network 192.168.0.0
address 192.168.0.2
netmask 255.255.255.0
gateway 192.168.0.1

# the secondary card connecting to the inside
auto eth0
iface eth0 inet static
name in-Facing Card
network 192.168.1.0
address 192.168.1.97
netmask 255.255.255.0
gateway 192.168.1.1
broadcast 192.168.1.255

# configure the port redirection that allows Tomcat to run as non-root
up /sbin/iptables -t nat -F
up /sbin/iptables -t nat -A PREROUTING -p tcp --dport 443 -j REDIRECT --to-ports
 8443

I suspect that the problem has to do with default gateways, which is where I get confused. My theory is that some packets that are meant to be returned to the wild WAN are getting 'shanghai'ed (i can say this, i'm living in China) into the local network. In fact, when the computer starts, the network auto-configures itself  such that the internal card is the default gateway, and no remote connections work. I have to manually bring down eth0 and back up again, to re-organize the gateways. This is the output of route -n when it is mostly working:
it@apps:~ $ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0
192.168.0.0     0.0.0.0         255.255.255.0   U     0      0        0 eth1
0.0.0.0         192.168.0.1     0.0.0.0         UG    0      0        0 eth1
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 eth0

As you can imagine, i have been tearing my hair out trying to solve this problem. Luckily, there are very few remote connections, and so they are content to try again later, but we are hoping to expand the remote access and we need to get it working better. Thanks fo anyone's help.

-Adeh

Long Live Ubuntu!

---

### Post by banadushi on 2005-08-03
Yea, the 2 gateway things will mess with stuff, here is how your config should look:

```

# The loopback network interface
auto lo
iface lo inet loopback

# The outward network interface
auto eth1
iface eth1 inet static
    name out-facing LAN card
    address 192.168.0.2
    netmask 255.255.255.0
    gateway 192.168.0.1

# the secondary card connecting to the inside
auto eth0
iface eth0 inet static
    name in-Facing Card
    address 192.168.1.97
    netmask 255.255.255.0
    # configure the port redirection that allows Tomcat to run as non-root
    up /sbin/iptables -t nat -F
    up /sbin/iptables -t nat -A PREROUTING -p tcp --dport 443 -j REDIRECT --to-ports
8443

```

Since your setup is a fairly simple one, I'd take out all the extra stuff and only have the address and netmask in each and the gateway only on eth1.  Having 2 default gateways will mess with the routing, if it wasn't so late, I could probly look up and actually explain why, but just suffice to say it "confuses" the network stack.

If there are servers/workstaions that will be accessing the server from a network other than 192.168.1.0/24 and 192.168.0.0/24 wich 192.168.0.1 does not know how to reach, but 192.168.1.1 does, you will need to route those networks to 192.168.1.1 such as:

```

# the secondary card connecting to the inside
auto eth0
    iface eth0 inet static
    name in-Facing Card
    address 192.168.1.97
    netmask 255.255.255.0
    up route add -net 10.0.0.0/8 gw 192.168.1.1
    down route del -net 10.0.0.0/8 gw 192.168.1.1

```

Have a good one!

Jason

---

### Post by adeh on 2005-08-03
Jason! You are my hero!

I thought that I needed the second gateway to find the db server, but as you said, I reconfigured and everything is golden. Now we just have to see if it stands up to the test of time.

Thanks again!

-Adeh

---

### Post by heimo on 2005-08-03
I just have to add my own respect to Jason for helping so well. I read your post, Adeh, and saw that problem is most probably two default gateways, but I was still thinking about correct configuration.

Really, Jason - nice job!

---

### Post by LordHunter317 on 2005-08-03
Actually, while the two default gateways is an issue, I'm not sure it's the issue causing hte timeout behavior the OP is seeing.

That doesn't make sense, as the routing table will use whatever route is first.

I suspect hardware problems, personally.

---

### Post by heimo on 2005-08-03
[QUOTE=LordHunter317]Actually, while the two default gateways is an issue, I'm not sure it's the issue causing hte timeout behavior the OP is seeing.

That doesn't make sense, as the routing table will use whatever route is first.
[/QUOTE]

That makes sense. These problems are sometimes hard to track (because of how randomly and relatively rarely it occurs) and configuration problems tend to cause systematic problems. Still I hope the problem was actually solved by the configuration change, but only time will tell.

---

### Post by LordHunter317 on 2005-08-03
[QUOTE=heimo]That makes sense. These problems are sometimes hard to track (because of how randomly and relatively rarely it occurs) and configuration problems tend to cause systematic problems. Still I hope the problem was actually solved by the configuration change, but only time will tell.[/QUOTE]
 Indeed.  But the rule of thumb is that the first thing you should do when you start having intermittent network outages is check the cables, then the NICs (usually by swapping them, you have spares, right? ;))

---

### Post by banadushi on 2005-08-03
[QUOTE=LordHunter317]
That doesn't make sense, as the routing table will use whatever route is first.
[/QUOTE]

Not neccessaraly.  The routing table is stored in hash tables, when you have 2 routes to the same network you get a collision in one of the entries in the hash table.  Since the kernel also does route caching, to prevent it from having to lookup every time from the hash table, the situation described is most likly the dual default gateway, and not hardware related.

Each time the routing cache updates, its probly getting the other result from the hash table, and then the default gateway flips back and forth.

When you print out the routing table with a command like `route -n`, it reads its data from the hash table, not from the routing cache, so you will see that the kernel has 2 default gateways listed in the hash table, but it will only ever use the one that is currently in the routing cache.

I'll put my money on the software configuration, before hardware.

---

### Post by heimo on 2005-08-03
[QUOTE=banadushi]
I'll put my money on the software configuration, before hardware.[/QUOTE]

I'm with you here. :) I still believe the problem was caused by two default gateway entries. I was suspecting it could cause some unexpected behaviour, but could have never explained what Jason just wrote - have to read it again some year ;)

But of course, the symptoms could be very well caused by badly behaving hardware. I'll still bet one Breezy install CD for software on this case.

As Jason seems to know a lot about this subject, is it possible to give metric value for default gateway? Would different metric values make this problem disappear? (not to say it would be sane configuration in this case)

---

### Post by LordHunter317 on 2005-08-03
[QUOTE=banadushi]Not neccessaraly.  The routing table is stored in hash tables, when you have 2 routes to the same network you get a collision in one of the entries in the hash table.[/quote]Yeah, and the routing table uses collision chaning.

Meaning that it's going to pull the first route of out the bucket, every time.  Routing hashtables are something where deterministic behavior is very much desirable.

---

### Post by az on 2005-08-03
A note to the audience here at Wimbledon:

You do not get "down-and-dirty" tech support like this on other forums, folks!


Cheers to all involved in this thread!

And now, back to the action...

---

### Post by adeh on 2005-08-03
Well, if the first 16 hours are so are any indication, the problem was certianly the 2 default gateways. The comment about storing gateways in a hashtable makes sense, because it really seemed that it was following some arbitratry schedule and turn on and off at will. If it was simply loading different values from the hashtable (although I don't know what the key might be) that would certianly give this sort of behavior.

As I said before, I had been running this setup for about 9 months, believe me, i swapped out the hardware multiple times. I was convinced that the problem was hardware. I had finally pretty much ruled that out though, and decided it was either in the config or at the ISP level.

Anyone know why this gateway stuff isn't deterministic?

---

### Post by banadushi on 2005-08-03
The linux kernel does not use standard bucket style linked lists for its collision chaining.  When you create a linked list in the kernel, you use its implementation as defined in <linux/list.h> if you want your code to ever be accepted by any maintainer.  To transverse a linked list the list_for_each() macro is used, wich takes 2 paramaters, a pointer to the current position in the list and the list.

So what I believe is happening, is that the default gateways are being set into the hash table as a linked list, then the first time the kernel needs to send something to them, it starts at the 0 position in the list and this gateway then gets cached in the routing cache.

From what I've read, and what I can gather from the source, the time between the flushing of the route cache is variable, under high loads it flushes less frequently.  Each time the cache is flushed, and we need to use the default gateway, it needs to be looked up again, but this time the current position is already set, so when we access the list the next time we get the next gateway listed, hence the intermittent flapping of the routing table.

Have a good one!

Jason

---

### Post by banadushi on 2005-08-03
[QUOTE=heimo]is it possible to give metric value for default gateway? Would different metric values make this problem disappear? (not to say it would be sane configuration in this case)[/QUOTE]

Well you can have multiple default gateways that have an equal weighted value associated with them, so in effect you will loadbalace the outgoing traffic to 2 different providers.  You do this by creating separate routing tables to handle talking to each provider and then give the tables a weighted value.  See [http://lartc.org/howto/lartc.rpdb.multiple-links.html](http://lartc.org/howto/lartc.rpdb.multiple-links.html) for the technical skinny on that.

This would not help in this situation, since you have the possibility of packets going out the wrong interface (although if you setup the split access as descibed above, packets should be nailed to the interface they came in on and will then go out that interface to that table's default gateway).

---

### Post by LordHunter317 on 2005-08-04
[QUOTE=banadushi] it needs to be looked up again, but this time the current position is already set, so when we access the list the next time we get the next gateway listed, hence the intermittent flapping of the routing table.[/quote]I'd love to see source code to support this, as that seems like the most retarded design one could pick.  It means you have to have extra code for when you fall off the end of the list to go to the start and try again.

---

### Post by banadushi on 2005-08-04
[QUOTE=LordHunter317]I'd love to see source code to support this, as that seems like the most retarded design one could pick.[/QUOTE]

All the relavent functions and macros concerning the lists are in [source_tree]/include/linux/list.h.  The specific implementation for the ipv4 routing table is in [source_tree]/net/ipv4/fib_*.c.

---

### Post by LordHunter317 on 2005-08-04
No, I want you to post a fragment that supports your argument.

Keeping track of where you were in a bucket's linked list in the routing table really makes no sense, implemetnation wise.  I want you to find and post a fragment that shows that the kernel really does save it's location in the linked list, and then uses that again later when it traverses the list again.

It really makes no sense for the kernel to do this: saving it's location in every list in the hash requires a worse case memory usage increase of O(n) (best-case table performance) and a best case of O(1) (worse case table performance).

That's why I'm skeptical.  I can't see why it'd save that piece of information and not just start at zero everytime.

---

### Post by dataw0lf on 2005-08-04
This is why Linux has not been suited for enterprise level routing.  The cache and the table are not kept synchronized 90% of the time.  Every time the cache flushes, the kernel rebuilds every route being utilized by traversing the hash/try table. Basically, if you miss in the cache, you have to go to the hash/try table, and since it's implemented with linked lists, this is where you're going to see all those collisions.

---

### Post by LordHunter317 on 2005-08-04
[QUOTE=dataw0lf] Every time the cache flushes, the kernel rebuilds every route being utilized by traversing the hash/try table.[/quote]Full cache flushes don't happen very often.  Linux has been able to flush portions of the routing cache for a long time.

>  Basically, if you miss in the cache, you have to go to the hash/try table,Right.  And you go through the policy engine and all that.  Your point?  Every other OS with a routing cache has to do the same thing.

>  and since it's implemented with linked lists,No, the buckets store their entries in a linked list.  The table itself is a regular hashtable.   Generally, the linked list should provide no overhead as you shouldn't have colliding entries.

And what else would you prefer them to use?  Red/black tree?  The routing table isn't large enough to make that be very beneficial, unless you had tens of thousands of routing entries.  In which case, you need specialized hardware *anyway*, so the software doesn't matter much if the hardware doesn't exist.

---

