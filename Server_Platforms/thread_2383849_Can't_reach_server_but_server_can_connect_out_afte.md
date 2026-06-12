---
title: "Can't reach server but server can connect out after latest update"
date: 2018-01-30
forum: Server Platforms
---

### Post by bikerjoe647 on 2018-01-30
I'm running 17.10 on an AMD with two nic cards that have been working fine since the 17.10 betas. These nic cards are connected via CAT6 to a gigabit switch. It is hosting a few websites via apache and tomcat. After the latest updates I can not ping nor reach these websites from any computer on the local network. The server itself can reach outside the network and these other local computers.

I have checked iptables and all of the policies are ACCEPT. I'm scratching my head on this one. Are there some logs I can check to see how it is refusing these connections?

---

### Post by wildmanne39 on 2018-01-30
*Thread moved to **Server Platforms, a more appropriate forum**.*

---

### Post by bikerjoe647 on 2018-01-31
I figured it out by trial and error. My managed switch was set for those two ports to be set up as link aggregated (LAG). It's been that way for about six months, not sure why the latest update didn't like that but all is well now. 

Still unsure how I could have detected this from the linux server itself.

---

### Post by TheFu on 2018-01-31
> **bikerjoe647 said:**
> I figured it out by trial and error. My managed switch was set for those two ports to be set up as link aggregated (LAG). It's been that way for about six months, not sure why the latest update didn't like that but all is well now. 

Still unsure how I could have detected this from the linux server itself.

Nobody here could help without more facts.  Network config files, routing info, and NIC configs.  Just too much to assume and ZERO mention of link aggregation in the first message.

When I first read it, I was thinking DNS issue and was going to ask if virtual hosts were the only issue or did direct IP work?

Glad you figured it out.  Networking in 17.10 uses different config methods.  I've seen other reports of issues, but since I only use LTS releases, don't expect to see that until 18.04 (probably won't load until July).

---

