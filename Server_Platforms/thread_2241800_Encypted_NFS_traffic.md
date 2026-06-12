---
title: "Encypted NFS traffic"
date: 2014-08-28
forum: Server Platforms
---

### Post by richard51 on 2014-08-28
I am using **autofs**, **ldap** (forced TLS) and **kerberos** (to authentication **NFS**).

I want all the **NFS** traffic to be encypted. The NFS security is currently set to **sec=krb5** on the client, and to **sec=krb5:krb5i:krb5p** on the server. Will setting the the NFS security to **sec=krb5p** on the client machine encypt the traffic between the client and the server? or do I need something else?

Thanks.

---

### Post by richard51 on 2014-08-29
Setting **sec=krb5p** on the client machines seems to do the trick, although the RPC headers are **not** encypted, the files and content are.

**Additional information:** File transfers using **krb5p** are around **70.5%** slower (*on my test network*) compared to using **krb5,** that's a massive performance degradation!

---

