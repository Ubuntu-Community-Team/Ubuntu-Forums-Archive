---
title: "how to check a network for monitoring"
date: 2010-09-28
forum: Security
---

### Post by jjakspaw6 on 2010-09-28
Is there a way to tell when network traffic is being monitored?

---

### Post by bodhi.zazen on 2010-09-28
It is a bad sign when the swat team show up.

Detecting such monitoring before the swat team shows up would be difficult to impossible.

---

### Post by jjakspaw6 on 2010-09-29
No, No swat team involved..... Nothing illegal going on.... I think that our corporate MIS Manager is causing grief in my office which is 1000 miles away from him.... 
My office is small. I've been managing the network for several years and I have had an open (COMMON SENSE) internet/Network use policy... (That is approved by our division president). 

This actaully never came up unitl a couple of weeks ago when they found out we are moving to our own division of the company...We have been noticing little some things stopped working. Its also things that have been said to me and the company president....    

Basically, we want to know if they are monitoring our traffic, with out accusing them of such.

---

### Post by BkkBonanza on 2010-09-29
If your traffic is routed thru their network then it is possible but it would be very hard to tell for sure. Monitoring should be transparent if done correctly. If it's causing problems then it could be due to configuration errors. I don't think it would be provable short of finding the traffic logs.

What would they be looking for? Evidence of using company resources for non-business use? Internal espionage? Maybe it's not monitoring but just some admin trying to sabotage your operations?

Did you notice changes in the routing of your traffic recently? There's just so many questions to ask. If you do traceroutes can you pin point new servers in the routes? This probably doesn't help if you don't have records of previous routes. Anyway, these are all things that come to mind.

---

### Post by jjakspaw6 on 2010-09-29
....I asked one of the Admins in our HQ office about monitoring. He confirmed that they are blocking sites at their end and monitor all traffic from our network to theirs... So... after a little closer look I noticed that he had configured DHCP to setup DNS only to the Server in their office..shortly after i made the change.... I got a call asking if we were having any trouble in my office.... :mrgreen:
 I cant stop the monitoring or anything else they do completely but at least I've made more of a pain in the backside for The MIS manager. 
Besides I only have to deal with the problem for another couple weeks when we come off their domain and back to our own.:guitar:

---

