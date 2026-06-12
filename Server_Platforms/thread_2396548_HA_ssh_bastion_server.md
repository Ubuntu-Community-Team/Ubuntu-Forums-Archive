---
title: "HA ssh bastion server"
date: 2018-07-17
forum: Server Platforms
---

### Post by kerryhall on 2018-07-17
Hello,

I want to set up an ssh server as a bastion server for my network.

I'm guessing the way this works is I'll set up two servers, install ssh server on both, have a floating ip, forward port 22 to that floating ip, then use something like keepalived to failover the floating ip.

Is keepalived the standard tool for this now? Or is something else recommended?

Thank you!

---

### Post by wildmanne39 on 2018-07-17
*Thread moved to **Server Platforms for a more appropriate fit**.*

---

### Post by TheFu on 2018-07-17
Seems like you are over thinking this.  If you want redundancy, have 2 ISPs provide connections to 2 different routers which port forward a high port (anything except 22/tcp!) to your 2 different systems running ssh. Don't use passwords. Only use ssh-keys or ssh-certs, and use something like fail2ban or denyhosts to block brute force attacks. If you don't use port 22, there won't be many attacks.  If you insist on 22/tcp, then expect thousands per hour.

Any users using ssh should be smart enough to have 2 IPs/hosts in their ~/.ssh/config for the connection.  They won't need to remember the port and all ssh-tools pay attention to that file already.  If you want to use it as a jump box, setting up this in the config file to make it automatic is easy too.

K.I.S.S.

---

### Post by kerryhall on 2018-07-17
Ok so I already have an ssh bastion I've been using for years. Keys only of course.

I just want it to be HA, as it's not a question of *if* hardware failure will occur, but *when*.

Yes I know router and ISP are single POF also, I'm working on that too, but that's not what I'm asking about here.

I'm already using denyhosts...but I don't understand, if I'm using keys only, how does that expose me to brute force attacks? Are they going to brute force my private key? I don't think there is any risk there...

Back to the issue at hand: what service is canonical for ip failover? keepalived?

Thank you!!

---

### Post by TheFu on 2018-07-17
[https://help.ubuntu.com/community/HALAMP](https://help.ubuntu.com/community/HALAMP) is the closest docs I found.

Wasted bandwidth for attacks is still wasted bandwidth.  Not having to review all those log entries is a good thing, IMHO.

---

