---
title: "Firewall with OpenVPN"
date: 2011-03-25
forum: Security
---

### Post by crashed111 on 2011-03-25
Hi

I want to use an OpenVPN connection on my laptop to secure Wireless connections. 

Laptop -->> Public Wi-Fi -->> Internet -->> OpenVPN Server in DataCenter

However on the client laptop I am having a job with the firewall. I want to have a drop policy on the INPUT and FORWARD chains (its going to be used on a public network so want to ensure I keep the laptop as safe as possible) and I just want traffic to pass over the tunnel interface. 

I have set rules on iptables to accept all traffic passing over the tunnel interface on both the INPUT and FORWARD chains and then set the policies on the chain as drop however I am having no luck.

When I change the policies on the chains to accept all works fine.

Searching around I haven't really found anyone who has managed to solve this problem. 

Any help would be much appreciated

Thanks guys

---

### Post by SeijiSensei on 2011-03-25
> **crashed111 said:**
> I just want traffic to pass over the tunnel interface.

You have to let the UDP traffic pass between the client and server.  Remember that the "tunnel" is really just a UDP stream between the two hosts.  You need iptables rules to permit each machine to see the other.  You'll also need to set up a point-to-point route between the two hosts and set the client's default route to use the server's tunnel IP as its default gateway.

---

