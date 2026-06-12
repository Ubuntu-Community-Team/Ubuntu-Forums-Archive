---
title: "Creating OpenLDAP group that grants SSH privileges to server"
date: 2011-09-28
forum: Security
---

### Post by sdmike6 on 2011-09-28
How do you created an LDAP group that allows SSH access to a server?

Right now if I make a LDAP account for a new user they also get SSH access to any server linked up to that LDAP server.

---

### Post by sdmike6 on 2012-04-04
It looks like turning off password authentication for ssh and sticking with keys is a better way to go.

---

