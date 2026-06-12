---
title: "not for profit datacentre"
date: 2012-04-01
forum: Server Platforms
---

### Post by maxalder on 2012-04-01
Hi  
 

 I need some advice on how to manage a small Data Center. I work for a small not for profit in Melbourne Australia. I have about 20 old Intel duel core servers that each are running a client's web application. Each client has there own server and will require a static IP address and I will need to measure their data downland and upload so that we can bill them for it. I have 2 adsl connections with 2 different provides for reliability.  I need something really simple with a good web interface and basic uses can use (I need to train their receptionist how to admin the system). I need it to load balance the two adsl links route through set static IP address and  something that can re-image each box on demand would also be good. Tall Ask I know but does anyone know of a FLOSS project that does this this.  
 

 Cheers  
 

 Max Aldermann

---

### Post by CharlesA on 2012-04-02
Train a receptionist to admin a data center server? What happens if something goes down? Do they just call you? That doesn't sound like a good idea (IMO at least).

Check out Nagios for monitoring the servers. What OS are these servers running?

---

### Post by rubylaser on 2012-04-02
> **CharlesA said:**
> Train a receptionist to admin a data center server? What happens if something goes down? Do they just call you? That doesn't sound like a good idea (IMO at least).


+1. This whole thing sounds like a recipe for disaster unless you're offering no Service-Level Agreement.  If so, I'm not sure who would pay you for hosting.

---

