---
title: "FreeRadius postauth"
date: 2013-12-09
forum: Server Platforms
---

### Post by nerdtron on 2013-12-09
Hi all,

So I have a freeradius server setup and mysql for its database of users and corresponding passwords. I also happen to have another table for users and their corresponding points/login credits.
What I want to do is to decrement a point from a user who authenticates with the freeradius server.
Example: 
User "John" (with 5 login credits) enters his credentials with password "testpassword". Since he is in the database of the radius server, he is given access. But I also want to decrement his login credits after a successful login.

Either freeradius can decrement the login credits by itself or just send a signal/script/command to another server/app to decrement the point is good enough for me. I just don't know to tackle this problem, any idea where to start?

---

