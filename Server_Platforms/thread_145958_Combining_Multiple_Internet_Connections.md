---
title: "Combining Multiple Internet Connections"
date: 2006-03-17
forum: Server Platforms
---

### Post by fsgpr on 2006-03-17
Is it possible to use an Ubuntu server with 3 network cards to combine two internet connections?  For example have a DSL connection in one card, a Cable Modem connection in card two, and a connection to the network in card three.  

The machine would need to allocate all network requests to one of the two networks (nothing sophisticated is needed in this case, sending requests from odd IP address to one connection and even to the other would be sufficient for our purposes).  It also should detect a loss of connectivity to on either connection and route all traffic over the remaing one if this condition is detected (so the two connections can serve as backups to each other in addition to increasing the effective bandwidth). 

Is this currently possible?  Any links to How-To's?  Or better search terms I could try to find more info on this type of solution?  

I am not sure where to start looking, and advice would be appreciated.


Thanks.

---

