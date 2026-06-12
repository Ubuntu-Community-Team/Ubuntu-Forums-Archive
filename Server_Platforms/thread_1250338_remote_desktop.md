---
title: "remote desktop"
date: 2009-08-26
forum: Server Platforms
---

### Post by didriksmidt on 2009-08-26
Hi, 

I have ubuntu server 9.04, and I only have access to it over ssh. I would like to view it through remote desktop aswell. As far as I can see the remote viewing is not installed or activated on the server.

is there any way of doing that through ssh?

---

### Post by jonabyte on 2009-08-26
do you have a gui desktop installed on the server, by default the server edition does not install one.

---

### Post by philcamlin on 2009-08-26
if  you install the gui you can then acess the server vis remote desktop

---

### Post by didriksmidt on 2009-08-26
Yes, there's gnome installed on it. But i'm pretty sure that it's not setup to receive connections.

---

### Post by jonabyte on 2009-08-26
try entering this:

```
vncserver
```

if it up and running you can use vnc to connect to the desktop.

---

