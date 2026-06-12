---
title: "Squid on a single NIC Ubuntu gateway"
date: 2016-09-24
forum: Server Platforms
---

### Post by jdoe111 on 2016-09-24
Hello, 

The following required setup is a bit confusing to me, and i hope someone can help shed some light:
Assuming I have on the same network and **same subnet **one dsl modem, a Ubuntu server with one network card, and a bunch of clients. I would like for my Ubuntu to be the gateway to my clients, and also to act as a transparent non-caching proxy with ssl support, AND content filtering via squidguard. Dont ask me why, but the modem gives out dhcp addresses assigning itself as a gateway to clients, and in the modem is created a routing rule to reroute all traffic headed to the modem back to the Ubuntu server.
PS: I plan to use squid 3.5 given the added https functionality.
PPS: users will be notified of the ssl interception, and lets assume there is no ethical issue here with https. also, im aware of the security risk this poses.

My questions are: 
1- Is what im asking for theoretically achievable? Ive never configured a gateway that didnt have seperate NICs for lan and wan before hence the confusion particularly in setting up iptables
2- is enabling ipv4 forwarding in sysctl.conf the only requirement for the primary gateway role? (before plunging into squid) or are there required iptables rules from the start?
3- given the routing rule mentioned above, do i still need to forward traffic from ports 80 and 443 to the equivalent squid ports using iptables?
4- does this setup eventually lead to clients being forced through the proxy (transparently and after installing the certificate) and being subject to the content filtering afterwards? 

Feel free to point out flaws in the concept of this setup and explain any wrong "ideas" present. however, i am forced to setup the gateway/proxy in this manner, so please point me in the right direction if its doable.

---

### Post by SeijiSensei on 2016-09-24
> Ive never configured a gateway that didnt have seperate NICs for lan and wan before hence the confusion particularly in setting up iptablesIve never configured a gateway that didnt have seperate NICs for lan and wan before hence the confusion particularly in setting up iptables

Why not just install another network card?  It sounds like you know how to make that work, and it certainly would be easier to set up.

---

### Post by jdoe111 on 2016-09-25
I wish that was an option but as i said, im stuck with this exact setup..

---

### Post by SeijiSensei on 2016-09-25
Then I suspect you're going to need to configure the clients to use the proxy manually.  Otherwise you'll need another box along the way to intercept outbound port 80 traffic and send it to the Squid box.  In order for transparency to work, the clients' default gateway needs an interception rule of some kind to redirect the traffic.

---

### Post by jdoe111 on 2016-09-25
All traffic headed to the DHCP assigned gateway was already set to be routed towards the ubuntu proxy as i mentioned before. Turns out it's pretty straightforward. Simply redirecting ports 80 and 443 to squid ports was all that was needed on the iptables, and the rest (squid, squidguard, etc.. ) was configured the same as with a normal setup. Thank you for your help :)

---

### Post by jdoe111 on 2016-09-28
i do have a question though. right now, my only iptables rules are the ones redirecting ports 80 and 443 to the squid ports, and that works just fine. however, when i try to either block a client completely by blocking the port 80 for his ip, make a client bypass squid by allowing the 80 port, or blocking a single port for the whole network, its not working. can anyone show me what how the proper configuration should look like?
as i said, the only iptables rules i have are:
iptables -t nat -A PREROUTING -p TCP -s 192.168.0.0/24 --dport 80 -j REDIRECT --to-port 3129
iptables -t nat -A PREROUTING -p TCP -s 192.168.0.0/24 --dport 443 -j REDIRECT --to-port 3130

---

