---
title: "Ports, Firewalls, Routers Noobie"
date: 2009-01-25
forum: Security
---

### Post by BlakeM on 2009-01-25
Ok, big noobie questions here. Just need to confirm a few things I've read:

1. The purpose of a router connected to an internal network is to prevent harmful information sent from an external network reaching devices connected to the internal network.

2. A router has ports that are either open or closed. The ports that are open or closed on a router can be configured by the Network Administrator. If a port is open, packets of data that are sent from external networks can pass through the port. If a port is closed, packets of data cannot pass through.

3. If the packets of data are passed through an open port, the router then routes the packets to the appropriate internal IP address.

4. A software firewall, like iptables, adds an extra layer of security on top of a hardware firewall. It will **filter** all packets that the computer receives from the router and determine if they are safe/appropriate. You can configure iptables to filter packets according to a set of rules. These rules can make sure that, for example, only packets that have been correctly identified as SSH packets are allowed through.

5. On a default "virgin" installation of Ubuntu 8.04 iptables is not enabled by default. However, no services are installed by default, so no programs are listening on any ports. If no programs are listening to ports, then you don't need to worry about a firewall?

6. Most routers close all ports by default. So, if I want to use a service like SSH, I have to open a port on my router (22 by default) to allow packets from an external network to be sent to the appropriate internal IP address. The external network, if behind a router, must also have its router configured to allow SSH packets and have them routed to the appropriate internal IP address. (Software firewalls at both ends must also be configured to allow and filter traffic on the appropriate port).

7. If I install services like Apache, SSH and MySQL, I should configure iptables and my router to allow these packets to pass through the appropriate ports. If I open these ports on my router, I should configure iptables to filter these packets to make sure malicious packets don't get through. I should also configure iptables to only allow packets from trusted external IP addresses. I should also set very strong passwords for authenticating use of these services and use public keys for SSH.

Ok, I've got a few other questions but I'll stop myself here. I'm pretty sure I've got a basic understanding. If any of this is wrong please let me know. I've been reading a lot of stuff on the Security forums. Just need a few things clarified. Thanks for taking the time to read and answer my questions.

---

### Post by BlakeM on 2009-01-25
Sorry, I've put this in the wrong thread/discussion. Can I move this thread? Or should I repost and wait 'til someone deletes the duplicate...I should probably have read Forum Rules more carefully.

---

### Post by cdenley on 2009-01-26
1. The purpose of a router is to allow traffic from multiple hosts to be routed through a single connection. An extra benefit is that it functions as a NAT firewall.

2. If a port is "open", then there is a host that will accept connections on that port. It may be a LAN computer, or possibly the router itself. If traffic is being forwarded to a computer which then drop or rejects the connection, the port technically isn't "open".

3. The router will forward incoming connections to the IP address you have configured it to forward to on that specific port. If you haven't configured that port to be forwarded, it will be dropped or rejected.

4. Iptables can filter (or route) traffic in all different kinds of ways. It doesn't identify that packets match a specific application, but can match based on protocol (tcp/udp), port, source, or destination. Iptables is typically configured by using a frontend like UFW or GUFW.

5. Iptables is "enabled" and configured to allow everything, but yes.

6. Traffic must be forwarded for that port on each NAT router on the server's side which user's must pass through in order to reach your server. Firewalls on the server side must allow the incoming traffic and the outbound traffic related to that connection. Firewalls on the client side must allow the outbound traffic and the inbound traffic related to that connection.

7. I'm not sure what "malicious packets" you're going to filter that your router doesn't, but yes. Iptables is also good for preventing brute force and denial of service attacks. Are you allowing mysql connections from over the internet? I would avoid that if possible.

---

### Post by The Cog on 2009-01-26
We're perhaps just arguing about names here, but:

1: The purpose of a router is to route packets to the correct network. For a router connected to only two networks, that reduces to simply passing packets back and forth as needed. It is not a routers job to filter harmful packets - that's the job of a firewall. A router may optionally implement Network Address Translation, which involves keeping track of what connections are using what addresses. NAT often only really permits connections to be established outgoing, so incidentally acts a bit like a firewall in that it prevents incoming connections.

2:
Again, that's a firewall function, not a router function. Also, calling firewall ports open or closed can be confused with whether a host has  ports open or closed. For a firewall, it is better (in my opinion) to say whether the packets are forwarded/dropped, permitted/denied. A host has its port open if it is listening for connections, closed if no application is listening. 

3:
If the packets are permitted by the (optional) firewall function of the router, then the router forwards those packets to the destination. It is possible that incoming packets won't correspond to any existing NAT translation entry and therefore get dropped because the router doesn't know where to forward them to.

4:
Exactly.

5:
Pretty-much. I would argure that iptables is enabled by default (you can't disable iptables) but is configured to permit all traffic both in and out. The default policy is to permit everything.

6:
Not really. Most routers permit traffic by default, unless they are routers with inbuilt firewall features. 

However, most home routers have to perform NAT translation from a private network address range that could accommodate typically 250+ PCs to a single public address. As a result, the router doesn't know where to route incoming packets unless an outgoing connection has already automatically established the translation table entry. An entry would typically equate the internal address/port where both the address and port can vary with a publicly visible address/port where the public address is fixed by the ISP. Incoming packets that don't match an enry in the table are dropped.

If you want incoming connections to be forwarded to a particular PC, you have to make a "static" NAT table entry, e.g. saying that incoming packets to the public address port 22 should be forwarded to a particular internal PC port 22. This is done for vary different reasons than configuring a firewall to permit packets to port 22, but happens to act pretty-much like a firewall would - you have to configure it to allow incoming connections to succeed.

7:
Iptables allows all traffic by default. If you install a server, you should perhas consider if you want the whole world to be able to connect to it, or whether you only want a few remote addresses to connect. For a web server, you probably want it visible to the world. In that case, there is nothing to configure iptables for - it already passes all traffic. For an SSH server, you may want it to only be reachable from work so all the password guessing bots can't keep trying. In that case, you may want to configure iptables to drop all incoming packets to port 22 unless they come from your work address. My home iptables config only allows SSH from work.

Some people like to configure iptables to drop all traffic by default. Many iptables configuring utilities like firestarter do this. It protects you against accidentally or unknowingly starting listening services. People think it can prevent viruses from phoning home or opening back-door ports, but I think any self respecting Linux virus would reconfigure iptables within milliseconds of getting control.

---

### Post by BlakeM on 2009-01-26
Thanks so much for your replies :).

I've made a bit of a mess though. I think this was the wrong place to post so I reposted in the Absolute Beginners Forum...sorry if I've made a mess.

---

### Post by adamlau on 2009-01-27
5. CUPS is listening on 631.

---

### Post by BlakeM on 2009-01-27
> **adamlau said:**
> 5. CUPS is listening on 631.

I read elsewhere that cups only listens for traffic sent from internal IP addresses...? Is that correct... or am I totally confused.

---

### Post by The Cog on 2009-01-27
Bhe command 
```
netstat -lnt
```
will tell you. If it's listening on 127.0.0.1:631 then it can only be connected to by the box itself. It it's listening in any other address such as 0.0.0.0 then it can be connected to from other boxes too. It's a configuration option somewhere in the cups config.

---

### Post by cdenley on 2009-01-27
> **adamlau said:**
> 5. CUPS is listening on 631.

If you want to get real picky, there are services listening for UDP connections by default, and not just on the local interface. I wouldn't be too worried about dhcp and avahi, though.

---

### Post by BlakeM on 2009-01-27
OK :). Thanks a lot for your help guys!

(Feels like I'm at studying two degrees at university: medicine and Ubuntu. So far I don't know which one is harder.)

---

