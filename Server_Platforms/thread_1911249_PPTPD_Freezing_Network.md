---
title: "PPTPD Freezing Network"
date: 2012-01-18
forum: Server Platforms
---

### Post by dr1134 on 2012-01-18
I am using Ubuntu Server 11.10 64 bit

I am trying to get PPTPD VPN working on it

I have tried multiply installation guides but each one I still get the same problem

When a client (Me on my laptop) connects, the network on the server freezes

When I try to ping say 8.8.8.8(The Google public DNS server) it will run though multiple pings before there is no  response back. The client is not on the Internet nor doing anything. It is just connected to the VPN server.

I thought that maybe this was the Google server how ever this is not the case. I started the ping and connected to the VPN and it reached 44 pings. I then tried it with out the client connected and it went beyond 44 pings. So I know that PPTPD is to blame for this.

I reinstalled the PPTPD server and the only configartion change were to the chap-secrets to allow a log in and the problem still happens.

I have no idea what is going on.

Any help will be much appreciated.

---

### Post by hackertarget on 2012-01-18
Just to confirm when you run ping from the server to google it continues ok with no VPN running (leave it for 5 mins to be sure)?

If so leave the ping running and connect to the VPN. Once VPN negotiation is complete is that when the ping fails.

Is communication over the VPN between client and server ok (even though external Ping is failing)?


Check routing tables on server before and after VPN connection. I am making a few assumptions but the servers default route should be the same.

---

### Post by dr1134 on 2012-01-18
I am still new to this whole Linux server stuff

How do you check the routing tables?

Also I think the communication over the VPN between client and server is ok. I can ping the server ok. Also system logs are not giving any errors about communication

I will also try redoing the ping test over 5 mins

---

### Post by dr1134 on 2012-01-18
Oh how I hate working on computers

So I run the ping test over five mins. It turns out that the network is freezing for proid of time when the client connects. It freeze for 2 or so mins and then works just fine.

So the question now is why?

If I have multiple clients connecting and disconnecting, then this is going to be a real problem

---

### Post by dr1134 on 2012-01-20
I have decided to change to a better vpn that better fits are needs and works

Thanks for all your help :)

---

### Post by SeijiSensei on 2012-01-20
> **dr1134 said:**
> I have decided to change to a better vpn that better fits are needs and works

Thanks for all your help :)

Good decision.  OpenVPN would be my choice.

---

