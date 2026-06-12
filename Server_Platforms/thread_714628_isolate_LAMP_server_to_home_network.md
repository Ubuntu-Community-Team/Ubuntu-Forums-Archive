---
title: "isolate LAMP server to home network"
date: 2008-03-04
forum: Server Platforms
---

### Post by jimmy the saint on 2008-03-04
I just installed Ubuntu Server with the LAMP option.  I do not want to allow access to or from the web.  What is the best way to allow my home networked computers to access it, but not the rest of the world?

I have Webmin installed.  I would still like to be able to download updates and such from the internet, I simply do not want the server functions, or the sites and software to be accessible outside my home network.

Thank You!!

---

### Post by faulkes on 2008-03-04
> **jimmy the saint said:**
> I just installed Ubuntu Server with the LAMP option.  I do not want to allow access to or from the web.  What is the best way to allow my home networked computers to access it, but not the rest of the world?

I have Webmin installed.  I would still like to be able to download updates and such from the internet, I simply do not want the server functions, or the sites and software to be accessible outside my home network.

Thank You!!

That depends on how your home network is setup.

If like many people you have a linksys/dlink/netgear type router,
by default you should be ok.  For those routers you must explicity forward
port 80 to the IP of the server.  In general, this applies to most other 
home/user level routers.

Faulkes

---

### Post by MjrNuT on 2008-03-04
If you have not forwarded port 80 in your router, you're invisible to the outside.

---

### Post by jimmy the saint on 2008-03-05
Outstanding!  Thank You Both.  I figured since I couldn't find anything easily be searching google it was probably a simple thing.

---

