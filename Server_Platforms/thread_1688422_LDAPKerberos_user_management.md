---
title: "LDAP/Kerberos user management"
date: 2011-02-15
forum: Server Platforms
---

### Post by chrism0dwk on 2011-02-15
Hi All,

I'm trying to migrate my (small) HPC cluster from NIS to LDAP/Kerberos, and have been following the (excellent) article in the Server Guide as well as the SingleSignOn community guide (for setting up a client).

I've got a test node up and running to allow ssh logins but have a couple of questions that Mr Google does not appear to be able to answer:

1)  Adding users: is it possible to create a user profile *and* password simultaneously, or am I stuck with adding a user to the LDAP directory first, then setting up the password using kadmin.local?  Ideally, it would be good to simply replicate the "adduser" command, since the LDAP, Kerberos, and NFS servers are on one machine.

2)  It appears that 'su' no longer works on the client machine, in that my root password is no longer recognised.  I see a line '+::0:0:::' if I do a 'getent passwd' which I think might be the culprit.  Is this the case?  Can I somehow enable 'su'?

Thanks,

Chris

---

