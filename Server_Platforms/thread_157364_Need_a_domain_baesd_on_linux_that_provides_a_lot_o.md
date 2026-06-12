---
title: "Need a domain baesd on linux that provides a lot of AD features."
date: 2006-04-09
forum: Server Platforms
---

### Post by Dalik on 2006-04-09
So this is a stupid question but here it goes anyway...

I have a windows AD domain setup, roaming profiles all working, but I would love  to move to a linux server.  Now I need to be able to "mix" linux and windows clients on this network, so file sharing(Samba).

The most important to me is "single sign on" for both linux and windows.  What options do I have for this?  I would like to be able to login against this directory, it could be via webmail and email logins etc.  I should be able to login once and my credentials be carried over and supplied for me for any new resource.  

I would also like to manage my resources with ACL and manage directory objects like groups and password and even profile paths locations.

I think I am asking for to much but what software that is free to use will provide this to me or most of it?  If you can please provide what application should be used for what feature.

Thanks,

Dalik

---

### Post by LordHunter317 on 2006-04-09
You can't do waht you want.  Linux can provide NT4 PDC functionality only, which isn't worth it.  Stay with AD.

---

### Post by N8MAN1068 on 2006-04-11
I tried the same thing...wasn't very successfull.
Integration is key.

For your best bet, look towards Novell for Suse/OpenSuse.

From what I understand, Xandros is the best distro to integrate w/ AD, but it isn't free nor do I have any personal experience with it.

---

### Post by ximok on 2006-06-09
We currently are using AD 2000 and ubuntu in a single sign on environment.

Our current hack involves using Kerberos and Winbind (slower).  I would prefer to use Kerberos and LDAP (faster), but the current issue with that is you need to install Microsoft's "unix tools for windows" to provide UID's and GID's that are unique (winbind will autogenerate on a per machine basis).  The issue isn't so much of installing the unix tools as it is manually assigning the UID/GID's to each user (I have 2500 of them).  So, until then, I'm sticking to Winbind.

The ldap authentication does provide some nice features such as allowing your email manager to use the the global distribution list and other cool stuff that goes with ldap.

---

### Post by dk_pa on 2006-06-09
Has anyone tried SAMBA 4 yet?  I know it's not stable I was just curious.

---

