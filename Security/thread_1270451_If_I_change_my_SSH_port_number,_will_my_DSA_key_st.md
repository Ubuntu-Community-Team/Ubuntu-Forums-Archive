---
title: "If I change my SSH port number, will my DSA key still work?"
date: 2009-09-19
forum: Security
---

### Post by mrcoulson on 2009-09-19
I want to change my SSH port number.  Will this require a new DSA key?  I'm working from home right now and don't want to accidentally lock myself out of the system until Monday morning.

Jeremy

---

### Post by falconindy on 2009-09-19
Your authentication key is recognized because you provided the public half to the ssh server. Changing the port won't affect this in any way.

---

### Post by kevdog on 2009-09-19
a resounding yes -- the key will still work.

---

### Post by mrcoulson on 2009-09-20
Hey, you guys were correct.  Unfortunately, however, I can't get in from outside the network now.  I believe I need to get our network guy to open my new port at the firewall.  Alas.  I suppose I'll do something else at home this evening.

Jeremy

---

### Post by kevdog on 2009-09-20
That or you could try reverse tunneling if no outbound ports are not blocked.  Yes it is usually more convenient to forward tunnel, but sometimes reverse tunneling can get you out of a jam also -- particularly if you have no control of the intervening firewalls.

---

### Post by mrcoulson on 2009-09-20
Dude, that would be wildly awesome.  I hate having to bug the already otherwise super-busy network guy.

How do I do that?  

Jeremy

---

### Post by i.r.id10t on 2009-09-20
Look at the -R option to ssh (instead of -L for local forwarding)

---

### Post by mrcoulson on 2009-09-22
I didn't get that to work, but he was glad to open the port for me.

Thanks!

Jeremy

---

