---
title: "Single login and home directory"
date: 2006-10-17
forum: Server Platforms
---

### Post by lutzky on 2006-10-17
My situation:

I have a Fedora server, which I'll call Albert (horribly configured in various ways, so I'd like to change as little as possible about it) and an Ubuntu server, which I'll call Bob (nice fresh Dapper server). 

Albert uses winbind to have a single-login with the Windows boxes, and hosts unix home directories for the users. I'd like Bob to have a single-login with that. Preferably without going through winbind, but rather authenticating against albert. I would like the home directories to be shared as well.

The solution I'm looking for should be

- Well-known, so plenty of online documentation would be available
- Simple to set up, especially on the server side (bonus points if it's something that's probably already installed on fedora)
- Reasonably fast
- Secure

Names I've heard in this direction would be AFS (a more secure NFS, as I've heard) and Kerberos (for the logins), but before I delve into installing such a thing, I figured I'd ask here on the forum. What would you recommend, and where can I get documentation?

---

