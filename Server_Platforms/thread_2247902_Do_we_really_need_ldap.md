---
title: "Do we really need ldap?"
date: 2014-10-11
forum: Server Platforms
---

### Post by richard51 on 2014-10-11
I was asked a question at work that made me think. A young intern asked, "if you use **Kerberos** for authentication and **LDAP** for authorization, but all you actually store in **LDAP** is basic user information (*id, gid, home dir, etc*), couldn't you just put */etc/passwd* and */etc/shadow* in a **NFS** share (*symlinked*) and remove **LDAP** entirely?" I have never thought about this, but maybe in a small home network something like this could be feasible to create a **SSO**?

---

### Post by Lars Noodén on 2014-10-11
I would think that those two files need to remain local.  Otherwise, if the network fails to come up or the NFS share is otherwise unavailable, it would be impossible for even the administrators to log in.  Usually when setting up kerberos/ldap you have fail over to local passwords, etc, for a few users just in case of such emergencies.  

Maybe the files could be rsynced or maintained in a version control system, distributed or othwise.  I guess it would also depend on the scale.  Are you talking about 10s, 100s or 1000s of users?

---

### Post by richard51 on 2014-10-11
Personally, at home and at work I use **Kerberos** for authentication and **LDAP** for authorization and various other things. I was just wondering if this was feasible... I suppose you could use scripts to determine if the network is down and alter the symlinks to these files accordingly. I personally need **Kerberos** and **LDAP**, but LDAP can be a pain for most people to use right (*really needs to be retired and replaced*). Whereas **Kerberos** is very easy to setup, but it still has to map to user accounts (*preferably, located in a central store*). I just wondered if the intern had something?

**Additional:** rsyncing those files, could be feasible. There is alot of id's and gid's that would have to match up, not just to the users, but also any and all the services on each machine, which may not be feasible and limit the network to linux only?

---

### Post by nerdtron on 2014-10-11
How may users? For home use only? I don't think the trouble of setting up and maintaining LDAP for a few users is worth the effort for home use.

---

### Post by richard51 on 2014-10-12
Home use, or small office, less than 10 PC's. I believe that **LDAP** has had it's day, and a total re-think for implementing a **S**ingle **S**ign** O**n environment is required.

---

