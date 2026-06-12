---
title: "Modify OpenLDAP entry for replication"
date: 2012-03-12
forum: Server Platforms
---

### Post by sgardne on 2012-03-12
I have successfully set up two OpenLDAP servers one as the master and the other replicating the masters database using the instructions in the ubuntu documentation, [here]("https://help.ubuntu.com/11.10/serverguide/C/openldap-server.html#openldap-server-replication"). What I'd like to do now is change the admin password on the master, but that will break the replication. How can I change the consumer configuration to update it with the new password?

Edit: I'm sure that using ldapmodify is probably what I want, I just don't know enough to do it correctly.

---

