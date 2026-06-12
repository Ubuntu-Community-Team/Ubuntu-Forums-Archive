---
title: "Port and service: why to filter"
date: 2010-12-19
forum: Security
---

### Post by narcisgarcia on 2010-12-19
Here I'm asking for a theoretical question, and not for practice recommendations. Everybody can answer "forget it, it's better to put a firewall and filter traffic by port", but I already know.

Usually packet filter is used to reject or discard petitions from network to a computer but, What happens if the computer is not listening?

That is to say, for example, someone can install a firewall that blocks packets for port TCP 80 (web), but if the computer hasn't any webserver to attend port TCP80, Which insecutiry is covering the firewall?

---

### Post by OpSecShellshock on 2010-12-19
Your impression is correct. If there is no running service that is listening for connections, then there is no reason to implement a utility to block those connections.

---

### Post by iponeverything on 2010-12-20
If you silently drop the packets for all non-listening ports, it will bog down port scanners.  

If the service is not listening and you are not filtering the packets the port scanner will get quicker results because of politeness of your box in sending ICMP control messages in response to connection attempt. 

Don't be nice to automated port scanners -- just drop the packets.

---

### Post by The Cog on 2010-12-21
When a computer receives an incoming connection request to a port that is not listening for connections, it will immediately send a connection refused message and the requesting computer knows immediately that it cannot connect. The connection refused message is an ICMP "Destination unreachable" message. 

If the firewall drops the connect request, the computer that sent the request must wait for a while, and only knows after a timeout that it cannot connect. Often the requesting computer will repeat the request a few times just in case a packet got lost by the network.

---

