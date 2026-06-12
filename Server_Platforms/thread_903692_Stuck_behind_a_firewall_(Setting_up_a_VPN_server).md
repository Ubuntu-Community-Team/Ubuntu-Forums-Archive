---
title: "Stuck behind a firewall (Setting up a VPN server)"
date: 2008-08-28
forum: Server Platforms
---

### Post by IQAndreas on 2008-08-28
Hello all.

I would like to set up a VPN server on one of my computers (linux or windows, does not matter), but I have a problem.

My ISP has all their clients (including me) behind their own firewall. Then, they lend out private IP addresses (in my case, 10.0.52.12) to all their clients. I also have a private firewall, but I can easily edit that or forward any ports as necessary. I would like to allow other people to access my server, but since I do not have a public IP address, would this still be possible?

Google searching just lead me to a bunch of really technical mumbo jumbo sites, and I'm not quite sure which of those sites applied to my situation.

I am familiar with basic networking (such as private and public IPs etc).

---

### Post by de0xyrib0se on 2008-08-28
No, you need a public routable IP in order for this to work, otherwise you cannot be reached.

---

### Post by IQAndreas on 2008-08-28
Darn.

If it helps, I have full access to the two computers that will be using the VPN connection, and I know that at least one of them has a routeable IP address. Is there still no way to do this?

Otherwise, I suppose I'll have to set up the server at my friend's house and use VNC to control it again. :( A huge pain in the neck.

---

### Post by jasonhuebert on 2008-08-28
If you can SSH to the two computers that would be using the VPN, you might be able to set up a reverse SSH tunnel.  This tunnel essentially pokes a hole in your ISP's firewall.

---

### Post by jasonhuebert on 2008-08-28
Here is a link describing what I am talking about.

[http://www.brandonhutchinson.com/ssh_tunnelling.html](http://www.brandonhutchinson.com/ssh_tunnelling.html)

---

### Post by yaztromo on 2008-08-28
IMO that is a horrible setup your ISP has used. Maybe changing ISP is the only way.

---

### Post by IQAndreas on 2008-08-28
Excellent. Thank you for the fast reply.

Will this work on Windows computers as well, or just Linux? Otherwise, would it be possible to place a linux computer inside their network which creates the tunnel, and then their windows computer can access the VPN server through the created tunnel?

---

### Post by de0xyrib0se on 2008-08-28
You are missing a very crucial point of that link, the reverse tunnel requires your home machine to be exposed to the world.

Unless you plan to have your home machine VPN somewhere else and then tunnel to localhost from that location which would bring up the already established tunnel from your house to that location which would have nothing to do with your initial question.

---

