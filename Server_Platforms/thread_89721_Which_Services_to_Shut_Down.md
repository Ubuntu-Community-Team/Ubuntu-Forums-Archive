---
title: "Which Services to Shut Down?"
date: 2005-11-13
forum: Server Platforms
---

### Post by kimvall on 2005-11-13
Which services do you recommend shutting down?

I essentially use my computer to surf the net, check email, watch movies, use Azureus, etc. I.e. it's you essential desktop PC.

Thanks in advance.

---

### Post by frodon on 2005-11-13
I would say all the services you don't need. 
Shut down the mail services if you don't need it, it's a good security increase.

---

### Post by kimvall on 2005-11-13
Would that be the mail fetcher (fetchmail) service?

The only list of services I can find is what's available from System -> Administration -> Services. But the list is very short... Is there a more complete list anywhere?

Thanks for the help!

---

### Post by frodon on 2005-11-13
Yes, you should disable fetchmail and postfix if you don't need them.

The list in System -> Administration -> Services is complete. At default ubuntu don't run a lot of services (that's why the list is short) but you may need to install some like samba, proftpd, ...

---

### Post by kimvall on 2005-11-13
Ok, excellent. Thanks again.

I can't find the postfix service though.

---

### Post by LordHunter317 on 2005-11-14
On an OOB install, there's no need to disable any services, because none are listening to the world.

---

