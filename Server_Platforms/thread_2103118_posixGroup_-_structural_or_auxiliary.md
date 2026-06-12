---
title: "posixGroup - structural or auxiliary?"
date: 2013-01-09
forum: Server Platforms
---

### Post by Philip Colmer on 2013-01-09
Hi

Following the instructions in [https://help.ubuntu.com/12.04/serverguide/openldap-server.html](https://help.ubuntu.com/12.04/serverguide/openldap-server.html) to set up my LDAP server results in the installation of nis.ldif which specifies the posixGroup objectClass as STRUCTURAL.

I need it to be AUXILIARY which I understand is the definition in the rfc2307 schema.

Am I able to make that change with data in the database or do I need to purge the LDAP server and start the installation again? Does the answer to that question change if I don't have any groups defined that are on objectClass posixGroup?

If I can make that change, what steps do I need to take, please?

If I need to rebuild the server, what do I need to change from the Ubuntu instructions in order to use rfc2307 instead of nis?

Thanks.

Philip

---

### Post by Philip Colmer on 2013-01-09
I'm going to mark this thread as solved although I don't quite have the information I need entirely.

In essence, though, it is not advisable to try and mess about with the schema once data is in the database. Since all of the data I've put in so far has been test data, I'm happy to wipe the database and start again, but that gives me a different problem and I'll start a new thread for that.

---

