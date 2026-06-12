---
title: "update manager freezes"
date: 2008-05-21
forum: Server Platforms
---

### Post by quikone8 on 2008-05-21
Server 8.04 will not download updates.  The alert manager indicates that there are 22 updates but once the manager is started it turns opaque and never gets to the password screen.  Is there a problem or did I do something wrong?

---

### Post by PmDematagoda on 2008-05-22
Open a terminal and execute:-
```
sudo apt-get upgrade
```
to see if you can install the updates that way.

---

### Post by uthturn on 2008-05-22
i was having the same problem and your suggestion fixed it :KS

edit: something weird i just noticed and i don't know if it's related but when i click on synaptic or software sources they do not load .

---

### Post by quikone8 on 2008-05-22
I noticed the same thing, synaptic freezes as well as update whether started from the task bar or from the menu.  I will try the suggestion and reply.  

Thankyou for your help.

---

### Post by quikone8 on 2008-05-22
I logged into the server remotely and the suggestion works great.

---

### Post by roadcone on 2008-05-23
Bump.

I am also having this problem with my desktop. But I am wondering if anyone knows why this is happening or how to fix it?

---

### Post by PmDematagoda on 2008-05-23
> **roadcone said:**
> Bump.

I am also having this problem with my desktop. But I am wondering if anyone knows why this is happening or how to fix it?

Did you try the command above?

---

