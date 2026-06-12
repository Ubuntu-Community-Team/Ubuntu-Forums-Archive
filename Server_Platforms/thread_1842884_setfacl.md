---
title: "setfacl"
date: 2011-09-12
forum: Server Platforms
---

### Post by Jay89 on 2011-09-12
Hey,
   So here is how my directory is set up.. **\\Samba-Server\DIR1\SubDIR1.** I have an end user that want's read and write access to **SubDIR1 **and only **SubDIR1** NO OTHER file in the **DIR1 **directory. How should I accomplish this? Is setfacl the best way? And if so, how? 

Thanks

---

### Post by Jay89 on 2011-09-12
One more thing, the user is part of a domain. They do not have an actual account on the Samba Server. I noticed a thread through a google search. Does this look right?

#setfacl -m u:domain\user:rwx

---

### Post by Jay89 on 2011-09-12
Got it. I forgot we had winbind enabled. so **#setfacl - R -m u:user:rwx** worked

---

