---
title: "Goof using usermod, lost Group memberships"
date: 2012-03-24
forum: Server Platforms
---

### Post by nosmadar on 2012-03-24
I was actually setting up subversion.
But I wanted to add my user to the subversion group via:
$ usermod -G subversion <user>

I did not realize that this would only make this user a member of the subversion group and remove all other gtoup memberships. I have since read about the -a option to append/keep the list of other group memberships.

My issue is that this was the 'Administrative' user for this server and I'm pretty sure it was a member of some other groups.  
Can any one tell me what groups an 'Administrative' user should be a member of so I can put them back.

Thanks!
(running Lucid sever)

---

### Post by matt_symes on 2012-03-24
Hi

> **nosmadar said:**
> I was actually setting up subversion.
But I wanted to add my user to the subversion group via:
$ usermod -G subversion <user>

I think you have realised this but...

> sudo  usermod -**a**G subversion <user>

> 
My issue is that this was the 'Administrative' user for this server and I'm pretty sure it was a member of some other groups.  
Can any one tell me what groups an 'Administrative' user should be a member of so I can put them back.

It depends on what you use your server for (i assume a server) but here are mine for the desktop.

```
matthew@matthew-Aspire-7540:~$ groups
**adm** cdrom **sudo** plugdev fuse lpadmin sambashare
matthew@matthew-Aspire-7540:~$
```

I'll certainly want adm and sudo. 

I expect you'll need these.

lpadmin for printers.
sambashare self explanatory.

You might want these.

Fuse for user space mounting of file systems.
plugdev and ccdrom for devices.

... and any others you may have had set up if it's a server such as www-data.

Kind regards

---

### Post by nosmadar on 2012-03-24
Thanks!
(And no, I had not figured out the format for the options - I was trying -G <newGroup> -a <existing,groups>

for the record here is the list of groups the user has once I got them restored:
<user> adm dialout cdrom plugdev sambashare lpadmin admin

Turns out that the groups command, when used with no other in formation, lists the groups assigned when the user logged in. And to check a change, the user would have to log off and log in again. 
Case Close.

---

