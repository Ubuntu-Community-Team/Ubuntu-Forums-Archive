---
title: "mobile broadband"
date: 2007-12-15
forum: Server Platforms
---

### Post by nightfrost on 2007-12-15
Hi all,

I have recently started to surf the net through a mobile broadband connection from Hi3G (Sweden), using a huawei e220 turbo-3g modem.

The thing is even when I reset all iptables rules and get:
```

 sudo iptables --list
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination
```

Port testing sites such as grc report "stealth" on all ports.

What's up with that? Is 3 stealthing all the ports? Is there any special deal with mobile broadband connections that I don't know of?

I'd like to be able to open ports if and when I want to open up ports.

---

### Post by koenn on 2007-12-15
a port will be "open" if you have a service (daemon) running on your computer that listens on that port. "
I'd like to be able to open ports if and when I want to open up ports." is a phrase without meaning. eg;if you want port 80 to be "open", run a webserver. 

Having all ports "stealth" is a good thing - you're invisible, except for those computers/servers **you **connect to (in which case, your computer will open a random port to establish the connection".

---

### Post by nightfrost on 2007-12-15
> **koenn said:**
> a port will be "open" if you have a service (daemon) running on your computer that listens on that port. "
I'd like to be able to open ports if and when I want to open up ports." is a phrase without meaning. eg;if you want port 80 to be "open", run a webserver. 

Having all ports "stealth" is a good thing - you're invisible, except for those computers/servers **you **connect to (in which case, your computer will open a random port to establish the connection".

Thanks for the reply.

Still, I don't understand why everything is stealth when all default policies are ACCEPT. For an average desktop system then, there's no point in defining various rules, DENY packets and so on?

But where I need a practical solution is this. When using bittorrent clients I need to have ports open, right? For incoming connections? How's that possible when all ports are stealth? I've tried azureuz's NAT/firewall test and it tells me:
```

 Connect attempt to X.X.X.X:45678 (your computer) timed out after 20 seconds. This means your port is probably closed.
```

I haven't had this problem previously with a normal ADSL broadband connection, that's why I'm wondering if this is realted to using a turbo-3g modem...

Thanks again.

---

### Post by koenn on 2007-12-15
I don't know Azareus, but the normal behaviour would be that if Azareus expects an incoming connection on port 45678, it will be listening on that port 45678, therefore, that port will be "open".
If it's not, either Azareus doesn't work correctly, or an other mechanism is preventing access to that port. Other mechanisms include :
- firewall rules (but you have ACCEPT policy and 'no rules' so that should work)
- a NAT router that, by the way NAT works, cuts of incoming connections unless the NAT router is configured to do "port forwarding". This should apply for a modem, unless its a modem/router combination. I looked at [www.tre.se/upload/3MobiltBredband/E220MAC.pdf](www.tre.se/upload/3MobiltBredband/E220MAC.pdf) , on first sight it's just a modem, but you should check because swedish is hard to read for me.
- your modem provides a dial-in connection, and you were offline
- your ISP filters certain traffic
- (probably overlooked a fewx others)

FYI
> Still, I don't understand why everything is stealth when all default policies are ACCEPT. For an average desktop system then, there's no point in defining various rules, DENY packets and so on?
if there's no sofware there to reply to GRC's connection attempts, you can ACCEPT all you want, but grc won't get any response, so they report "stealthed'. And yes, for normal desktop systems (without any software that would accept incoming connections), DENY rules (in INPUT) are useless. If you do need to allow incoming connections, usually you'd DENY everything by default, but e.g. ACCEPT traffic coming from certain addresses and/or ports, or traffic going to certain addresses/ports, or a combination.

---

### Post by nightfrost on 2007-12-15
Thanks a lot for your reply. It's very educative for me!

Nevertheless, something seems to not be the way it should here. Following what you write, a program that listens to a port in effect opens it. This is what I would expect. For example, I've always used port 45678 for bittorrent traffic. So a bittorrent client configured to use that port for incoming requests should open that port. I have now tried this with a few bittorrent clients and all claim that the port defined is closed. A few of the clients I've tried have builtin options to test this, and they all respond "closed", whereas they didn't when I was connected through ADSL/cable or anything non-"mobile broadband" (never used ppp-stuff before though!).

Also, I'm pretty sure the huawei e220 is nothing but a modem (well, it acts as USB-disk as well, but that's beside the point here of course).

So, I think there's a problem somewhere, I just don't know where. I just know that 3 do funny things sometimes (not funny ha-ha, but funny-boo-hoo).

---

### Post by koenn on 2007-12-15
I think I'm missing something here, but I can't put my finger on it.
It doesn't make sense to me that a program would be listening on port 45678, and a connection comes in, why would it complain that port is closed in stead of just acknowledge the incoming request and establish the connection ? 

Are we talking about the same things here ?

---

### Post by koenn on 2007-12-15
I installed Azureus and had a look at it. Like you said, it does lets you set a "TCP Listening port" and test it. So we *are* talking about the same thing
Mine failed with "NAT Error" because I'm behind a NAT router. It passed when i forwarded incoming connections and at that point, grc 'shields up' also finds the port to be open, as expected. 

so, seeing that the firewall on your PC would accept incoming connections, and assuming that your torrent client(s) don't do any filtering by themselves (maybe check that ?), the only explanations I see at this point are that
- there's a filter / firewall / ... somewhere further down the line, eg at your ISP, or
- there's something peculiar about ppp that interferes here. That is rather unlikely, as the torrent application just uses IP adresses and tcp/ip ports, so it doesn't really matter if that runs over ppp, ethernet, or homing pigeons.

---

### Post by nightfrost on 2007-12-15
I found the problem!
The default APN does not provide a public IP. I found an alternate APN to use which does precisely that. When I use the alternate APN grc detects close ports (no stealth) and Azureus et. al. claim the ports to be open.

This is good, cause this has forced me to play a bit with iptables and learn some more. I'm using some rules now in order to be in stealth mode and I allow ports that I use for bitorrent clients to be open. Very nice.

But this leads me to another question:
First off, this is what I use to ACCEPT connections for bitorrent:
```
iptables -I INPUT -p tcp --dport 45678 -j ACCEPT
iptables -I INPUT -p udp --dport 45678 -j ACCEPT
```

But I also share the connection of this computer to another, usin masquerading like this:

```
iptables -t nat -A POSTROUTING -o $WAN -j MASQUERADE
```

This obviously gives NAT errors (similar to what you described) on the other computer. Now, how do I forward tcp & udp requests to that computer. Any ideas?

I really appreciate you taking me through this. I've learned a lot about iptables and networks the last 24 hours or so!

---

### Post by koenn on 2007-12-15
I did 
```
 iptables -t nat -A PREROUTING -p tcp --dport 30045 -j DNAT --to 192.168.10.110:30045
iptables -t nat -A PREROUTING -p tcp --dport 30045 -j DNAT --to 192.168.10.110:30045

```
it means : send tcp | udp packets that arrive at this machine's port 30045 to address 192.168.10.110, port 30045

I tried to refine it a bit with specifying an input interface, but i couldn't get the syntax right. maybe you'll have to work on it a bit. I don't remember exactly in what order the chains (INPUT? FORWARD, PREROUTING, POSTROUTING, ...) are processed so I don't know if this will interfere with the other torrent rules. You may need to specify destination addresses to get it al working


what's an APN ?

---

### Post by nightfrost on 2007-12-15
Thanks! I'll start off with your suggestions and try to play around a bit with that.

> **koenn said:**
> 
what's an APN ?

Well, I'm not completely sure as I'm new to the whole mobile broadband thing, but I think it's a sort of access point used in GPRS and 3G connections. It's the same thing used in cell phones for WAPing.

---

