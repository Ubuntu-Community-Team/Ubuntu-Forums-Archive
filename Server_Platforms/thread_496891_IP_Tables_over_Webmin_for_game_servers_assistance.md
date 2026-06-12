---
title: "IP Tables over Webmin for game servers assistance"
date: 2007-07-09
forum: Server Platforms
---

### Post by MianoSM on 2007-07-09
*

---

### Post by koenn on 2007-07-10
I don't use webmin so I'm not familiar with the "user-friendly" translation of the firewall rules, I'll just assuming they're iptables statements.

There's a few things unclear, maybe you can clarify

You're running 7 servers, so "my server" is what you call a web server ? Not the 6 game servers ? and the web server needs to be able to ping the game servers ? 

What do you mean by 'the "reject all" is blocking the connectivity on my server" ? 

firewalls usually distinguishes between inbound and outbound traffic (and iptables als knows "forward"). your rules don't say whether they rule in- or outbound traffic. Does webmin tell you anything about that ? 


Given all that, the following can be hardly more that a wild guess, but:
-- I don't see any rule that allows echo-request. Is it possible that the pings are blocked from leaving the machine ? 

-- Could the targets of your ping be blocking or ignoring ICMP ? 


Besides that, 
"Accept If protocol is TCP and TCP flags ACK (of ACK) are set " --> where did you get that from ? Isn't that included in state=RELATED, ESTABLISHED ? 

and for "the ability to connect to ports 27015 through 28000, and I'm not sure if the connection is a TCP, or a UDP,", why not allow these ports for both tcp and udp then ?

---

### Post by MianoSM on 2007-07-10
Yes, I was incorrect in my description.

The "Box", is actually running more then just one service/server.

The box has 4 nic's and all 4 need to be pingable, which I'm assuming is a ICMP and type is echo-request?
I'd rather not allow all connections via ports 27000-28000 so I'm going to have to research those ports and their usage further at the moment....

Reject always simply shuts down all other network traffic that isn't above stated in the "Allow" statements.

---

### Post by koenn on 2007-07-10
> **MianoSM said:**
> 
Reject always simply shuts down all other network traffic that isn't above stated in the "Allow" statements.
Well, yes, that's what it is meant for. 

a 'ping' is an ICMP echo-request, and the expected answer is an ICMP echo-reply.

I still don't see your network layout, so it's hard to evaluate the firewal rules. 
Try to describe it in such a way that I (or others) can picture it an understand which host should connect to what other host.

---

### Post by MianoSM on 2007-07-10
The network layout is beyond me somewhat beacuse I'm not 100% sure which ports are being used, and/or how they are being used by the game servers.

They are configured to connect to Game Manufacturer servers, and then allow the home users connect to the game server itself.....

So I have 
SSH running
http/apache2 running
mysql running
webmin running 
and 6 games.

When I run an nmap -sS localhost from the box itself this is what I get:

Starting Nmap 4.20 ( [http://insecure.org](http://insecure.org) ) at 2007-07-10 17:01 EDT
Interesting ports on localhost (127.0.0.1):
Not shown: 1692 closed ports
PORT      STATE SERVICE
22/tcp    open  ssh
80/tcp    open  http
631/tcp   open  ipp
3306/tcp  open  mysql
10000/tcp open  snet-sensor-mgmt

---

