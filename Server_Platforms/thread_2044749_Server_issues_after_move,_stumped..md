---
title: "Server issues after move, stumped."
date: 2012-08-19
forum: Server Platforms
---

### Post by Watchlord on 2012-08-19
I used to have my server running like a dream. I had a website and Minecraft server running on an old HP Proliant dl380 g3. All web traffic was forwarded to NIC1 (192.168.1.20) and all Minecraft traffic was forwarded to NIC2 (192.168.1.21). I was using a crappy Netgear router.

I recently moved and switched to a Linksys WRT54G running dd-wrt (loopback able build). A new router, different ethernet cables, and the server going without power for 3 days is all that I can see that changed. It was tested and working fine before it was packed.

I can no longer access the website (I haven't tried Minecraft), I get a connection timeout with 192.168.1.20.

What I've tried:
IE and Firefox
Acessing the website through 192.168.1.21
Restarting the Apache (gives no errors)
Flashing the router with different dd-wrt builds.
Flashing the router with Tomato.
Removing the router and connecting the clients via a switch.

What I can do (more reasons I think it's not the router):
I can ping 192.168.1.20 and 192.168.1.21 from my client pc.
I can access the iLO interface (192.168.1.25) with no problems.
I can use other devices on the network (like my printer).
I can see the connection to the server in dd-wrt
I can access the internet from either NIC, and I can get to the website using 192.168.1.20 while on the server.
I can host a Minecaft server on a client pc and access from another client pc on the network. 

I've spent about 8 hours troubleshooting, I'm almost ready to start just shooting.](*,)

---

### Post by LHammonds on 2012-08-19
Do you still have access to your old crappy netgear?  Have you tried different cables just for grins and giggles?

LHammonds

---

### Post by Watchlord on 2012-08-19
I don't have the old netgear' and the cables include the old ones. I have tied every cable combination.

---

### Post by CharlesA on 2012-08-19
Try a direct connection from the client to the server and see if you can connect from inside the network.

---

### Post by Watchlord on 2012-08-19
Like with a crossover cable NIC to NIC?

---

### Post by CharlesA on 2012-08-20
Yeah.

That will rule out the router itself. ;)

Question: How are you trying to access the services from outside the network? If the ports are set up right and you are sure the IP hasn't change, it should "just work"

---

### Post by Watchlord on 2012-08-20
> **CharlesA said:**
> Yeah.

That will rule out the router itself. ;)

Question: How are you trying to access the services from outside the network? If the ports are set up right and you are sure the IP hasn't change, it should "just work"

I will try the crossover. I've tried the routers WAN ip, doesn't work either. iLO works fine externally though, so the port forwarding is right.

---

### Post by CharlesA on 2012-08-20
If you are trying to use the WAN IP from inside the network that might not always work.

It works for me on DD-WRT, but I know most home routers don't support that sort of connection.

The crossover cable is just to test to make sure you can connect to the machine, then you can worry about the router. ;)

---

### Post by sandyd on 2012-08-20
> **Watchlord said:**
> I will try the crossover. I've tried the routers WAN ip, doesn't work either. iLO works fine externally though, so the port forwarding is right.
Have you tried simply enabling NAT to the Server ip?

---

### Post by Watchlord on 2012-08-20
Ok, I tried with the crossover cable. Same problem. Also, If I try to ping 192.168.1.20 I get "Reply from 192.168.1.7: Destination host unreachable." Just to test the crossover I connected it to the iLO port. iLO worked perfectly over crossover. 

Keep in mind, that while the server is in the usual setup, the server and the router show 192.168.1.20 connected. I can ping the port from the clients. I can access the internet while using the server through 192.168.1.20.

---

### Post by Watchlord on 2012-08-21
So I was sitting there thinking and staring that conky on the server's desktop. After a few minutes the mighty god of networking compelled me to change my netmask.

Sooooo......It works now guys. Thanks. I'm going sit in a corner and feel stupid now.

---

### Post by CharlesA on 2012-08-21
Happens to everyone. Glad you got it sorted out. :)

---

### Post by LHammonds on 2012-08-21
I typically do at least 3 to 5 stupid things each day.  Most usually go completely unnoticed by anyone. :P  It happens to everyone.

I've never fat fingered a net mask before...always have used Class C and been really lucky.

I've messed up IP addresses plenty of times though.

LHammonds

---

