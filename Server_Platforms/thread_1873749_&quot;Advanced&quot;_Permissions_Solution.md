---
title: "&quot;Advanced&quot; Permissions Solution"
date: 2011-11-01
forum: Server Platforms
---

### Post by jmacgowan on 2011-11-01
I would like to set some "special" permissions for some folders in a SAMBA share, but I'm not sure what the best practice would be.

Let's say I have three users: U1, U2, and U3.

All of the users have a share mapped to their home directory.

I would like a setup where U1 can access U2 and U3's home directory via Samba, but U2 and U3 cannot access each other's home directory.  

I suppose that I could just add U1 to the U2 and U3 groups, but as I expand this into a larger system, that will require quite a bit of upkeep.

Am I stuck with just doing this all manually (or write a script to do it) or is there a better way?  Maybe setting an "Admin" for particular SAMBA shares?

Thank you in advance for your time.

---

