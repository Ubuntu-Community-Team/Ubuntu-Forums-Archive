---
title: "SSH tunneling troubles"
date: 2012-07-17
forum: Server Platforms
---

### Post by jasbur on 2012-07-17
I'm trying to route VNC traffic between 2 firewalled computer using SSH tunneling. Initially I tested this inside our network routing through out local server.

Computer 1 has an IP address of 10.0.0.102 and the VNC server running on port 5910. It's connecting to the local server using:
```
ssh -R 56788:10.0.0.102:5910 user@10.0.0.1
```

Computer 2 is has an IP address of 10.0.0.103 and is running the VNC client. It's connecting to the server using:
```
ssh -L 5910:127.0.0.1:56788 user@10.0.0.1
```

I then tell Computer 2 to connect to the VNC server on 127.0.0.1:5910 and everything works great being routed to port 56788 on ssh, then back to 5910 on the other side.

When I try to do the same thing through an external server, say somethingsomething.com the exact same way everybody connects but the traffic doesn't seem to route and VNC doesn't connect. I am substituting the public IP address of computer 1 in it's connection string too, for the record.

Is there some sort of routing consideration I'm missing or something here?

---

### Post by Mr.Dee on 2012-07-17
Are you behind a router?

---

### Post by jasbur on 2012-07-18
Yes, both computers are. That's the goal, to get VNC to connect 2 computers behind routers without port forwarding.

---

### Post by SeijiSensei on 2012-07-18
There's no way I can think of to accomplish this without port forwarding or without using a third, public server.  I would use OpenVPN for this task, but the situations are identical.  On one side I can configure a machine as a client so it can talk through the firewall.  On the other side, there has to be a publicly-visible address:port to which the client can connect.  The situation is no different with SSH.

The only possible solution I can think of is to employ a third, publicly visible machine as a common router.  Set up tunnels from each client machine to this third one and add routing rules for traffic between the two sides.  All my OpenVPN tunnels terminate at a common public machine (a Linode) and, for some pairs of tunnels, traffic is routed between them.

---

### Post by jasbur on 2012-07-18
Actually, that's the ultimate plan, to have a third publicly visible and un-firewalled server to coordinate the traffic. I can get both to connect and set up the tunnel on each end. I just can't get them to route to eachother.

You mentioned setting up routing rules. I think this is where my problem lies. Where and what would I change typically to facilitate this sort of traffic?

---

