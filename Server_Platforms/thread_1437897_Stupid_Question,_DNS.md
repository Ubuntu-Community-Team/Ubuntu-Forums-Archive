---
title: "Stupid Question, DNS"
date: 2010-03-24
forum: Server Platforms
---

### Post by terrapin893 on 2010-03-24
So I have everything going to have my dns setup on my home machine, but I am still not able to get my domain names to resolve.  I have created and registered the host names (nameservers) I have created all appropriate NS and A records in my zone file, but then it occurs to me . . . my friggin ISP blocks port 80.  So my assumption is that there is no way that I will be able to have the nameservers resolve with the incoming http port blocked . . . and thus there will be no way for people to load my zone file so there will be no way that my site resolves . . . correct?  

Its about time to find another ISP . . . .

---

### Post by jrssystemsnet on 2010-03-24
DNS does not use port 80; DNS uses port 53.  It can use either TCP or UDP, so it's generally best to forward both to the server.

---

### Post by terrapin893 on 2010-03-24
thats good news . . . . and something that i should have known.

---

### Post by KB1JWQ on 2010-03-24
Eh, no worries.  Turtles have historically had problems with DNS. :-D

---

