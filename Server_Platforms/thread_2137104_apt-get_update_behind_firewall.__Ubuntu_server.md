---
title: "apt-get update behind firewall.  Ubuntu server"
date: 2013-04-19
forum: Server Platforms
---

### Post by amalgamas on 2013-04-19
I have set up a ubuntu server 12.04 behind a D-Link DFL 160 firewall.

After a lot of googling I have opened (I think, I am a little unsure to exactly how this is done in the DFL160) ports 22, 80, all ports over 1124 etc.  

No matter what I tried apt-get update stalls, i let it run for a day, stopped it when it reached 10500 get-tries.

I took the server home and connected it to my home network (firewall only in router) and apt-get ran without problems.  

Question: what configuration do I have to do in the DFL 160 firewall to get apt-get working?

---

### Post by CharlesA on 2013-04-19
You shouldn't have to do anything because apt-get uses http to fetch packages.

Are you sure the firewall isn't restricting outbound communication on port 80?

---

### Post by amalgamas on 2013-04-20
> **CharlesA said:**
> You shouldn't have to do anything because apt-get uses http to fetch packages.

Are you sure the firewall isn't restricting outbound communication on port 80?

Yes, port 80 is open both ways, inbound and outbound.  There must be someting else

Thanks for your response!

---

### Post by darkod on 2013-04-20
What Charles meant is, outbound communication is usually open by default. You shouldn't need to open any incoming ports, that way you are opening your server to possible attacks.

Most firewalls would let through traffic originating from inside the network. As for traffic originating from outside, that it what needs to be controlled by the firewall.

You have another issue, maybe with routing, dns settings, etc. As you see yourself, even opening port 80 in both directions didn't help. The issue is not the firewall.

iIf you have a static IP setup on the server, did you also specify dns servers to use? On the server, If you try to ping 8.8.8.8 for example, does it work?

PS. Even if in your firewall you have to open outgoing traffic, you don't open incoming ports like you did. Opening all incoming ports (or most of them) makes no sense having a firewall, right?

What you need to do is open outgoing traffic for destination port 80 (the destination of the traffic on the ubuntu servers), and that the firewall allows all traffic established from your network, when it comes back. That will make the firewall allow all replies, while still keeping ports closed for other people.

---

### Post by amalgamas on 2013-04-20
> **darkod said:**
> What Charles meant is, outbound communication is usually open by default. You shouldn't need to open any incoming ports, that way you are opening your server to possible attacks.

Most firewalls would let through traffic originating from inside the network. As for traffic originating from outside, that it what needs to be controlled by the firewall.

You have another issue, maybe with routing, dns settings, etc. As you see yourself, even opening port 80 in both directions didn't help. The issue is not the firewall.

iIf you have a static IP setup on the server, did you also specify dns servers to use? On the server, If you try to ping 8.8.8.8 for example, does it work?

PS. Even if in your firewall you have to open outgoing traffic, you don't open incoming ports like you did. Opening all incoming ports (or most of them) makes no sense having a firewall, right?

What you need to do is open outgoing traffic for destination port 80 (the destination of the traffic on the ubuntu servers), and that the firewall allows all traffic established from your network, when it comes back. That will make the firewall allow all replies, while still keeping ports closed for other people.

Trying to solve an annoying problem i am willing to test every possibility one being opening incoming ports.  I shut them afterwards, so the firewall is intact.  I am not at my work right now, but I am quite sure the DNS-settings are ok and that I can ping 8.8.8.8.  I will post /etc/network/interfaces

---

