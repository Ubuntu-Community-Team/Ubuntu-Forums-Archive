---
title: "User Authentication for Sometimes Connected Users"
date: 2007-03-06
forum: Server Platforms
---

### Post by sanicki on 2007-03-06
i want my cake and to eat it too. is there any known configuration that would let me authenticate my users and store their profiles and files on a centralized machine BUT still allow them to log in and have access to their files locally when offline?

i'm thinking openldap and rsync? is there a better way? anyone done anything similar?

suggestions appreciated.

scenarios:
1. user in office or connected by broadband. login is verified against openldap. user accesses his files remotely. files and pw sync with local copy periodically and/or on shutdown.
2. user has no internet access. login is verified against local machine. user accesses his files locally. files and pw sync with network copy on next connect.
3. user has limited connection (aka the grail). login is verified against openldap. user accesses his files locally. files and pw sync with network copy periodically and/or on shutdown.
4. user quits. password is changed on centralized machine. local pw file syncs on next boot (and/or shutdown). once rebooted, user no longer has active pw. (better: local files deleted too.)

---

### Post by kidders on 2007-03-06
Hi there,

Centralised authentication (by definition) presupposes access to a centralised authentication database. In that sense, your question is a little contradictory. :-( Even if it were possible, the idea that their authentication information would eventually wind up being stored on everyone's machine would quite rightly make your users very uncomfortable.

> **sanicki said:**
> is there a better way?

There is no reason not to run centralised and local authentication schemes in parallel. You could, for instance, opt for LDAP- and shadow-based mechanisms, and let your users switch between them, depending on whether they wanted access to a local or centralised account.

Most centralised systems involve a certain amount of this kind of thing anyway ... for example, it would be a little strange to require users like syslog, lp, or root to waste time constantly validating their access privileges against a central LDAP server.

---

### Post by Mr. C. on 2007-03-07
I presume you are looking for a Windows Active Domain type of configuration, which meets all your requirements.

Windows caches the domain password locally for offline authentication, and the Windows desktop and computer can be hardened and locked down to protect against unwanted user changes - this is all done via administrative group policies.  Being a very complex system, I'm not aware of any comparable open source or *nix implementation, but I'm certainly no expert here.

Let us know what you find!

MrC

---

### Post by sanicki on 2007-03-07
Mr. C,

Nail on the head. I'll post back if I find anything.

---

