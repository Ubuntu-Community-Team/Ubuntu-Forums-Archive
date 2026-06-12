---
title: "Jabberd2 - User Accounts Created Although Inband Registration Is Disabled"
date: 2014-01-17
forum: Security
---

### Post by Kirk Schnable on 2014-01-17
I have seen something troubling recently on my Jabberd2 server.  I have in-band registration disabled, and attempts to register in-band with various clients result in a redirection to my network web page.

Yet two accounts mysteriously appeared on my server.  They were not registered through my web registration form, they were registered in-band.  sm.log confirms this:
> **"sm.log"]Tue Jan 14 00:10:59 2014 [notice] created user: jid=pedrqqxz@mydomain.com
Thu Jan 16 10:18:08 2014 [notice] created user: jid=jz1gx1v2@mydomain.com[/QUOTE]

The accounts don't look like they've been used heavily, though a user did sign into them.  The IP looks like a web hosting company.
[QUOTE="c2s.log"]Tue Jan 14 00:10:59 2014 [notice] [13] created user: user=pedrqqxz said:**
>  [13] registration succeeded, requesting user creation: jid=pedrqqxz@mydomain.com
Tue Jan 14 00:10:59 2014 [notice] [13] [::ffff:37.157.196.67, port=33890] disconnect jid=pedrqqxz@mydomain.com, packets: 2
Tue Jan 14 00:11:00 2014 [notice] [13] SASL authentication succeeded: mechanism=DIGEST-MD5; authzid=pedrqqxz@mydomain.com, TLS negotiated
Tue Jan 14 00:11:00 2014 [notice] [13] bound: jid=pedrqqxz@mydomain.com/yP4Vz1
Tue Jan 14 00:11:00 2014 [notice] [13] [::ffff:37.157.196.67, port=33892] disconnect jid=pedrqqxz@mydomain.com/yP4Vz1, packets: 11

Thu Jan 16 10:18:08 2014 [notice] [10] created user: user=jz1gx1v2; realm=mydomain.com
Thu Jan 16 10:18:08 2014 [notice] [10] registration succeeded, requesting user creation: jid=jz1gx1v2@mydomain.com
Thu Jan 16 10:18:08 2014 [notice] [10] [::ffff:37.157.196.67, port=40607] disconnect jid=jz1gx1v2@mydomain.com, packets: 2
Thu Jan 16 10:18:09 2014 [notice] [10] SASL authentication succeeded: mechanism=DIGEST-MD5; authzid=jz1gx1v2@mydomain.com, TLS negotiated
Thu Jan 16 10:18:09 2014 [notice] [10] bound: jid=jz1gx1v2@mydomain.com/moW9Vq
Thu Jan 16 10:18:30 2014 [notice] [10] [::ffff:37.157.196.67, port=40608] disconnect jid=jz1gx1v2@mydomain.com/moW9Vq, packets: 403

Any idea how or why this happened?  I don't want registration in this manner to be allowed on the server, that's why I turned it off.

---

