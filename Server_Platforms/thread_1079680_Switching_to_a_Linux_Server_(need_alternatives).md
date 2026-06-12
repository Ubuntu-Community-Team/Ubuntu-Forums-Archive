---
title: "Switching to a Linux Server (need alternatives)"
date: 2009-02-24
forum: Server Platforms
---

### Post by linorics on 2009-02-24
I'm trying to get as far away from Windows as possible, but I lack the terms need to find the alternatives. So any help or suggestions would be great.

So my background I have couple of years with Linux and are extremely versed in using it. 

**Current**
Users are logging onto computers and saving there files on a network share(Windows). We have about 50PC for users to use, however each pc is assigned to one or two people. And I have to setup all of the share access manually. 


**Goals**
**1.) A server that has all users stored in a "Directory"**
[INDENT]So if a user's password is changed, it is also changed on all of the clients or if I need to add a new user I don't have to add it on 50+ PC's.[/INDENT]
**2.) All of there PC's are clients that have "Roaming Profiles"**
[INDENT]So if a user logs into PC a, b or c they can have access to there personal files and group files.[/INDENT]
**3.)A way to change the users access to group files **
[INDENT]So if we have group students and student a,b,c. they can all have there own files and student group files, and i have the ability to remove users from that share. [/INDENT]

When I was talking to a Microsoft rep he said that Windows is that only operating system that do all of the listed requirements, but I don't think that is true. So if you could give me some advice of what I should be looking into I would love it.

---

### Post by freerkkalsbeek on 2009-02-24
Checkout LTSP (Linux Terminal Server Project) which is part of the Edubuntu installation. That has all you need.

Another option is using FreeNX and ThinStation on the connected PC's, but for maintenance considerations I'd prefer LTSP.

Maybe consider putting the users in LDAP, but not required.

Freerk

---

### Post by Yashiro on 2009-02-25
You want to use Linux for what? As the server and client or just server?

---

### Post by pdtpatrick on 2009-02-25
You are talking about creating an environment that allows central authentication ?? 

You can use samba to create an Active Directory like environment and you can incorporate it with openLDAP and kerberos. 

Then each user can log in and their own profile would be created just like a windows environment.

---

### Post by drzolo on 2009-02-25
1) OpenLdap should do the trick, phpldapadmin is a useful web interface . Do 2 servers with ldap for redundancy
2) Samba, we have about 40 + winxp users with roaming profiles.
Also might want to get 2 servers both mirroring each other and heartbeat running between each other. NFS mount the servers on your samba server. This way when one goes down, things are still good.
3) This one is Samba, with groups in OpenLdap, setup samba with shares that only allows access to certain groups.


This is a big job, but once you get it running is very low maintenance.

---

### Post by koenn on 2009-02-26
what drzolo said.

You might consider installing posix acl, these give you a fine grained file permission system not unlike the one Windows uses (and compatible with it but not entirely the same) in stead of (or combined with) the unix-like user-group-world read/write/execute permission bits.

If you do this entirely Windows style, with everything on 1 computer, I think you might even manage to have Samba handle all user authentication, without LDAP Directory. But I'm not entirely sure, you'd have to look that up. And everything on 1 box is not necessarily a good idea.

---

### Post by linorics on 2009-03-12
Perfect! This is exactly what I needed. I can tell this will take a lot of research and work. 

Do you know of any good tutorials on setting up this Centralized Access?

---

