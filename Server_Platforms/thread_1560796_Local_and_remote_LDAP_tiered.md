---
title: "Local and remote LDAP tiered?"
date: 2010-08-25
forum: Server Platforms
---

### Post by tomviolin on 2010-08-25
I have multiple servers located within a research facility that is part of a college campus.  I currently have the main server configured to authenticate users using the campus-wide LDAP.  However, there are a set of accounts used for group logins, as well as for maintenance and administration of the server, that only exist on the server.  The user authentication smoothly and transparently uses the local passwd/shadow database as a fallback if authentication fails at the LDAP level.  I am very satisfied with this setup, as far as a single server goes.

I would like to share the local users among several servers.  However, since I'm already using LDAP to authenticate campus-wide users, I'm wondering if there is a way I could implement my own local LDAP and then configure things such that the server would first try the campus LDAP, then fall back to the local LDAP, and then finally fall back to the passwd/shadow database.

Is this possible?

Thank you!

---

