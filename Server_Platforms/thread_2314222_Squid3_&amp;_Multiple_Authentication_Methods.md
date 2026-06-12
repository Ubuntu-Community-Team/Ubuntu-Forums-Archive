---
title: "Squid3 &amp; Multiple Authentication Methods"
date: 2016-02-19
forum: Server Platforms
---

### Post by david140 on 2016-02-19
Hi folks

Was just looking for some advice if it possible to use multiple authentication methods when using Squid3.

Here is what I am looking to achieve in order of preference:

1) Trusted IP Listed via ACL (If IP Address Match, can use Proxy and does not require credentials)
2) Not on Trusted IP List ACL? Request Username & Password Authentication instead.
3) Can’t provide credentials on incorrect details provided? Deny access.

I have already set-up the ACL which works, and have already set-up the Username & Passwords using just one specific method at a time, although can you combine both methods within the config file itself to get the above result required? 

Thanks in advance for any appreciated support that can be given to help me out. 

David :)

---

### Post by SeijiSensei on 2016-02-19
Take a look at this: [http://wiki.squid-cache.org/SquidFaq/SquidAcl#Common_Mistakes](http://wiki.squid-cache.org/SquidFaq/SquidAcl#Common_Mistakes)

It discusses and/or logic in acl's and access controls.

---

### Post by david140 on 2016-02-20
> **SeijiSensei said:**
> Take a look at this: [http://wiki.squid-cache.org/SquidFaq/SquidAcl#Common_Mistakes](http://wiki.squid-cache.org/SquidFaq/SquidAcl#Common_Mistakes)

It discusses and/or logic in acl's and access controls.

Thank you - Resolved with little fuss :D

Thanks a Million ;)

David

---

