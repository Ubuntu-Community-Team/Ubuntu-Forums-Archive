---
title: "Microsoft also knows windows server sucks, according to netcraft lol :)"
date: 2008-05-22
forum: The Cafe
---

### Post by eragon100 on 2008-05-22
[http://uptime.netcraft.com/up/graph/?host=download.microsoft.com]("http://uptime.netcraft.com/up/graph/?host=download.microsoft.com")

You would expect microsoft to run microsoft windows server on their on own servers, now wouldn't you? :lolflag:

---

### Post by bimmerd00d on 2008-05-22
something tells me it is runnign IIS on Linux?  What?

---

### Post by Moustacha on 2008-05-22
er........how?

---

### Post by Delever on 2008-05-22
Forgive my ignorance, but how IIS can work on Linux?

---

### Post by Mathiasdm on 2008-05-22
This is simply because they asked Akamai to do load balancing for them, and the Akamai servers run Linux.
The Microsoft servers do run IIS on Windows.

---

### Post by Chame_Wizard on 2008-05-22
the irony :lolflag:

---

### Post by bimmerd00d on 2008-05-22
> **Delever said:**
> Forgive my ignorance, but how IIS can work on Linux?

Just what it says in the link the OP posted.  unless i'm reading it wrong.

---

### Post by Dr. C on 2008-05-22
This has been happening for quite a while. Basically Microsoft is running IIS on Windows Server but the Windows Servers are behind  GNU / Linux firewalls they contracted out to an outside party, so from outside the firewall it looks like IIS is running on GNU / Linux. 

One could argue that Microsoft fears their Windows Server boxes are going to be hacked so they hide behind GNU / Linux firewalls for protection.

---

