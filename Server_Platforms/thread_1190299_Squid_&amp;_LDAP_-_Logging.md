---
title: "Squid &amp; LDAP - Logging?"
date: 2009-06-17
forum: Server Platforms
---

### Post by the_jaymz on 2009-06-17
Hi Everyone,
I have about 150 users on 3 Win2k3 terminal servers. I've been told to let them access the web from these servers, so I've got them going through squid. Now I'm just wondering if I setup LDAP-based authentication against my AD domain, will the access.log show usernames?
As it is right now, it only shows the IP addys of the 3 terminal servers.
Upper management is going to want someone to yell at if something bad happens, and I'd much rather direct them to the person who actually caused the problem that take it on the chin because I don't have logs.
Any help or info would be great.
Thanks

---

### Post by the_jaymz on 2009-06-18
For the record, yes, if squid authenticates users against AD, it will put the usernames in the log files.

---

