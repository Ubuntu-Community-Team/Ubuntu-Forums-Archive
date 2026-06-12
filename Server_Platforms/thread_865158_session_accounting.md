---
title: "session accounting"
date: 2008-07-20
forum: Server Platforms
---

### Post by a-linux-user on 2008-07-20
hi everybody;
I have a small LAN cmposed of debian server (NFS LDAP), with ubuntu 8.04 and win XP as clients.
for he authentication I use the ldap.
Is it possible to use freeradius (AAA)to count the time for each user per day and then define a kind of quota, that's mean for each, user i want to define how much of time per day he can use his session, passing the quota the user session is closed until the next day.
 if this is possible can anyone tell me how or give me a link to some tutorial.
thank you in advance.

---

### Post by sadara on 2008-07-20
I'm probably wrong, But I don't think you can do that.
I different method would be to create a PPTP/PPPeE server on you box, and monitor the time on the inbound connections.

---

