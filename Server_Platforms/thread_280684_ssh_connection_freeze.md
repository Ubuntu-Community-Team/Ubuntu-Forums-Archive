---
title: "ssh connection freeze"
date: 2006-10-19
forum: Server Platforms
---

### Post by Zarin on 2006-10-19
I recently installes Ubuntu server 6.06 on an old pc that I want to use as a router for my home network. When I connect to the server using ssh the connection freezes after some time. It does not recover or timeout or anything. The server is still alive and I can open another session that will work for some time until it also freezes. 

Does anyone know what could be wrong?

---

### Post by gnufied on 2007-01-25
Oh goodness I am having similar problem.

---

### Post by PetePete on 2007-01-25
you sure its not timeouting?
if you use putty, click on connections, and set second between keepalives to 30

that solved a similar problem i had.

---

### Post by boast on 2008-04-18
I also have the same problem

(sshing to my dads ubuntu desktop)

---

### Post by Dr Small on 2008-04-18
On the SSH server, run this and tell me if KeepAlive is set to "Yes":
```
cat /etc/ssh/sshd_config | grep "KeepAlive"
```

---

