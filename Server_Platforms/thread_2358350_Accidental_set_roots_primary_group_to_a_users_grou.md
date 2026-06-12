---
title: "Accidental set roots primary group to a users group"
date: 2017-04-12
forum: Server Platforms
---

### Post by alforddm on 2017-04-12
In the process of setting up a new ubuntu 16.04 server, I accidentally set roots primary group as a users group.    Thankfully, I still have sudo access.   I've edited the /etc/groups file to show [noparse]root:x:0:[/noparse]  and restarted the server.   However my root mysql account no longer has access.   
Is this something that is fixable or should I just redo the server?   

There are is one mysql database that I would like to retrieve if possible.

---

### Post by alforddm on 2017-04-12
Well, after spending all morning googling still not getting access to MySQL I just nuked the whole thing and started over.  Thankfully, I had only moved and updated one smaller site.

---

### Post by TheFu on 2017-04-13
Or restore from proper backups.

---

