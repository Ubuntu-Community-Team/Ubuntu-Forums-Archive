---
title: "Restrict access on Samba PDC"
date: 2008-04-15
forum: Server Platforms
---

### Post by robsic on 2008-04-15
Hi, 
I need to restrict domain logon for some users to certain WinXP hosts, i.e. I want a particular user to be able to do a domain logon only on his own machine, not the others. I guess that you somehow have to associate a user account with a machine account in order to do this.
Is there any way to accomplish this by changing the Samba configuration?

I'm grateful for any answer (and sorry if I missed an earlier post on the topic):)

BR,

Robert

---

### Post by cdenley on 2008-04-15
I don't think you can configure who can log in to which client from the server, but you can configure which users/groups can login to each client with the client's local group permissions.

---

