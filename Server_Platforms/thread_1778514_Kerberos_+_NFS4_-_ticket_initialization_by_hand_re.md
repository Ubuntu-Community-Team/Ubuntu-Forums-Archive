---
title: "Kerberos + NFS4 - ticket initialization by hand required"
date: 2011-06-09
forum: Server Platforms
---

### Post by lafayette on 2011-06-09
Hi all,

a week ago I correctly setup an environment with a Kerberos5 KDC (MIT) and, on the same machine, an NFS4 server.

Things worked flawlessly, the server had a principal in KDC and in its own keytab, and so for the client.
Normal user could access mounted directories following the permissions set on files (and idmapd worked correctly).

Now, since yesterday, I noticed that user can't access no more directories (even those owned by them): I tried some debugging and noticed that, if I add a principal (in form of username@REALM) and request a ticket with kinit, things get working again.

I don't know what's happened, I just imagine that the credentials for the machine would be enough to mount and access the NFS share as was for the first days of my setup.

Any hint on what to investigate?

---

### Post by lafayette on 2011-06-09
More hints and evidences: seems that user can't access the machine ticket for nfs. Is that default behaviour? 

There's no selinux context on client

Here the logs of rpc.gssd:

```
Jun  9 11:53:37 host rpc.gssd[4512]: getting credentials for client with uid 1100 for server XXXX
Jun  9 11:53:37 host rpc.gssd[4512]: CC file '/tmp/krb5cc_machine_XXXX' being considered, with preferred realm 'XXXX'
Jun  9 11:53:37 host rpc.gssd[4512]: CC file '/tmp/krb5cc_machine_EXXXX' owned by 0, not 1100
Jun  9 11:53:37 host rpc.gssd[4512]: WARNING: Failed to create krb5 context for user with uid 1100 for server XXXX

```

---

