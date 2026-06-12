---
title: "Monitor network"
date: 2012-04-04
forum: Server Platforms
---

### Post by Rakeshvijayan on 2012-04-04
Hi all,

Friends I have setup a lan connection .with the ip rage of C class address and have a internal server for our library .whole system except one system uses dansguardian proxy for Internet .I can monitor whole system by dansguradian logs except one system .I need to monitor that exception system ,because some times our Internet may slow ,I think they uses torrent on that system, they uses the full bandwidth ,I configured that system not hiding the gateway  .Is there any solution to find what they do Internet ........

Thanks

---

### Post by arrrghhh on 2012-04-04
Seems silly to leave one machine exposed like that, but if you don't have any other choice - why not see what your router/gateway provides?  Depending on what the hardware is, there are many options.  Cisco and other gateways can provide netflow data, routers that support DD-WRT have some basic bandwidth monitoring and QoS scheduling capabilities available.

---

### Post by Rakeshvijayan on 2012-04-04
Friend I don't need to change any setup now ,that why ask help ......is there any way to depend on any software ...


and also if use nat is it possible to monitor ?

---

### Post by arrrghhh on 2012-04-04
> **Rakeshvijayan said:**
> Friend I don't need to change any setup now ,that why ask help ......is there any way to depend on any software ...


and also if use nat is it possible to monitor ?

I don't know how to respond to this... what?  I don't know what you're asking.  You've been very vague, and I'm not quite sure what you're looking to achieve.  All I know is it's probably easier to analyze the traffic thru the actual gateway that is carrying the traffic to the internet - or lock down access to that machine better so it can't do things like download torrents (which is what you seem concerned about?)

---

### Post by Rakeshvijayan on 2012-04-16
My question is out of technical that is not discover yet .discovered solution is only hack that system  .

Thanks friend my question is worth less that I under stand now by posting this thread ...........

---

