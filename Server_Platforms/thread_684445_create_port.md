---
title: "create port"
date: 2008-02-01
forum: Server Platforms
---

### Post by bigie on 2008-02-01
hy all,
I have create aplication on my win and for connect to my ubuntu server I used port 9876, but how can I create new port on my ubuntu box?

please help me :(

---

### Post by MJN on 2008-02-01
The listening/server application on your Ubuntu machine needs to be configured to listen on that port.
 
Can you explain in more detail what you've got, and what you're trying to achieve? This will help us give a more meaningful specific answer.
 
Mathew

---

### Post by bigie on 2008-02-01
thank's for your reply, and sorry for my bad english...

ok I want to make a new port in ubuntu for example port 9876, and I will  use this port for connect to my ubuntu from my wind.

---

### Post by koenn on 2008-02-01
you don't *create* a port out of the blue.
A port is created when a program (on the server) creates a "socket", i.e when a program (on the server) starts waiting for connections at a given port, and is willing to accept connections to that port, then you have a "port". In the code of the program, the port is just a number between 1 and 65535. 

Can you explain in more detail what you've got, and what you're trying to achieve? This will help us give a more meaningful specific answer.

---

