---
title: "How to Stop/Remove Email Server from Ubuntu Server 9.04"
date: 2009-10-11
forum: Server Platforms
---

### Post by cybershan on 2009-10-11
I recently installed ubuntu server 9.04 on a fresh install and I picked the 'lamp server' and the 'email server' options during startup.

Now , I want to remove/stop all the traces of the email components. How can i do this? 


Thanks in advance.

---

### Post by BQAggie2006 on 2009-10-12
From the command line, run:
 
```
 sudo tasksel
```
 
Un-select the Email Server task and hit Enter.

---

### Post by cybershan on 2009-10-12
Thank you very much, BQAggie2006.

---

