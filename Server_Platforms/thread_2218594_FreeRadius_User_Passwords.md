---
title: "FreeRadius User Passwords"
date: 2014-04-21
forum: Server Platforms
---

### Post by thomas.l.hull on 2014-04-21
Hello, I am using FreeRadius as authentication for the network (switches and routers). I want to add new users to the server. I was wondering how can I set it for when a new user logs in for the first time,  the server to prompt them to change the  password? 

Also is there a way to view /etc/freeradius/users without being able to read the users new personal passwords?

Thanks in advanced!

---

### Post by nerdtron on 2014-04-21
I'm not aware on how to solve your first problem.
The second problem can be solved if you use a database such as MySQL and encrypt the passwords there. Or you can always secure the /etc/freeradius/users file so that nobody other than the owner and freeradius can read it contents.

---

