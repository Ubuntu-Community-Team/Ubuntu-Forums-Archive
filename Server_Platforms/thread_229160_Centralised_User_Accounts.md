---
title: "Centralised User Accounts"
date: 2006-08-04
forum: Server Platforms
---

### Post by Bezdomny on 2006-08-04
Hi,

Being new to (K)Ubuntu and all things Linux but jumping in feet first and offering to save a friend a bundle on license fee's I offered to install a Linux based network in his business (there's a bet in place that I don't want to lose as it involves being Naked, vindaloo, copious amounts of Guinness, a traffic cone and a stopwatch :-P ). Ok, the problem and forgive the MS references:

How do you centralise the user accounts? In the MS environment (no spitting please) I would create an AD (domain) and add the users into group on there, then on the client set to log on validated on the domain. Permissions can be set against the domain accounts not local ones. Is it possible in linux/ubuntu? :confused: :confused: 

Also, using NFS shares and mounting through fstab I managed to get the connections to work, reconnects and write access. Even though I got it to work I couldn't understand why. There was no correlation between the account on the client and the account on the server apart from the IP mask I allowed on the share. Does this mean that any user of the client can modify the files on that share? When creating a folder on the share from the client I noticed it created it under a server local account (again with no link to client account), why?

I'm not asking for a full solution here, just point me in the direction of a mud pit full of FAQ's and throw in some URL's and I'd be happy as a kid in a sweet shop with a pocket full of change. Or am I barking up the wrong tree here or even in the right forest?

Specifically referring to Ubuntu server if there's anything around I can read through the noob goggles I'd be grateful. 

Many thanks.

---

### Post by Jabran Asghar on 2006-08-04
Hi,

You may consider using LDAP + Samba, to configure Linux Box as Primary Domain Controller (PDC). Perhaps it will not be a full replacement of Windows AD, but still will serve the purpose of managing user accounts, profiles, files server, etc. 

I am on the same track now adays, following may help. Though its for RHL, but would be easy to adopt for Ubuntu.

[http://www-128.ibm.com/developerworks/edu/l-dw-linux-ldapsamba-i.html]("http://www-128.ibm.com/developerworks/edu/l-dw-linux-ldapsamba-i.html")

Jabran

---

### Post by Bezdomny on 2006-08-07
Manyt thanks for that, definately pointed me in the right direction. OpenLDAP seems to do the trick.

Steve.

---

### Post by Jabran Asghar on 2006-08-21
Hi,

Just wondering if you tried something like "Roaming profiles" for Linux desktop clients?

And if you got any ideas about [this]("http://www.ubuntuforums.org/showthread.php?t=238903") thread.

Thanks. 

Jabran

---

### Post by backu on 2006-09-01
Hey,
   Started to follow the guide on the IBM site, however I've ran into a problem... I don't seem to have samba.schema located anywheres on the system, and make install on the IO::Socket::SSLeay errors out massivly.. am I just missing something on this?

---

