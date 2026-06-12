---
title: "I am unable to connect my Domain to my Server"
date: 2020-04-23
forum: Server Platforms
---

### Post by lukarius on 2020-04-23
So i have am trying to use ubuntu to setup my minecraft server, but whenever the server tries to connect to the domain it will not connect. I'm pretty new to this software and don't know too much about it.T
The ubuntu server it is supposed to use the domain "play.cataclystmc.com"
Here is a link to what my NameCheap Domains advanced DNS settings look like. 
[[IMG]https://ibb.co/dDv48CG[/IMG][IMG]https://ibb.co/dDv48CG[/IMG]https://ibb.co/dDv48CG]("https://ibb.co/dDv48CG")

I'm not sure if this is enough information to solve my problem so i will provide more information if you ask for it.

---

### Post by darkod on 2020-04-24
Unfortunately I think the info provided doesn't explain much, at least not to me.

First of all, we are not talking about Active Directory domain here, right?

Then, what exactly does "connect my domain" means? If we are talking about public internet domains and dns, that is not the phrase to use. The image seems to show dns records.

But what is the point and the actual problem? Do you need to point the A record to your server public IP?

---

### Post by TheFu on 2020-04-24
[https://blog.jdpfu.com/2010/11/05/what-you-need-to-have-a-web-site](https://blog.jdpfu.com/2010/11/05/what-you-need-to-have-a-web-site) provides some background on the requirements to have an internet domain available to the world.

So, please confirm you have all 3 things purchased and configured together.
That DNS points at : 24.0.69.102 ..... is that correct?
The DNS record:
```
play.cataclystmc.com.   1770    IN      A       24.0.69.102
```
I did a quick port scan to see which ports were open. Appears that none are open.  That requires changing the WAN router and the firewall on your server.
Post back and we can work through this.

---

