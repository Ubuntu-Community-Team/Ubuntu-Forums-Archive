---
title: "Kerberos and hierarchical authentication"
date: 2010-01-08
forum: Security
---

### Post by boredboy on 2010-01-08
I am looking to setup a centralised server to do all authentication on our linux network.  We have several subnets that I would like to keep separate.  I have successfully got a test kerberos and ldap install working with several clients all authenticating to the main server.  However all these clients all belong to the same realm.  I would like to have the different subnets authenticating to different realms, but off the same centralised management server.  Finally, just to be awkward I would like it that if authentication on the sub realm fails, it falls back to checking the parent realm (or vice versa).  I'll try give an example below to illustrate what I'm talking about.

We have a management machine with kerberos/ldap installed.  Then (for simplicity) we have a web cluster and a database cluster.  We have three realms created.  EXAMPLE.COM is the parent, WEB.EXAMPLE.COM and DB.EXAMPLE.COM.  I would like any accounts on EXAMPLE.COM to have access to both WEB and DB.  An account in WEB can only access boxes in that realm, similar with DB.  The idea behind this is that a main sys admin just has to be added to the parent realm to have access to the entire network, while db and web developers are locked to their set of machines.  I'm not even sure this is possible on a single kerberos server and haven't found a single doc online on how it could in theory could be setup.  If anybody has any ideas, links, experience etc that could help, please let me know.  Thanks in advance

---

### Post by Lars Noodén on 2010-01-09
It sounds like you are setting up two or more realms.  You *could*, I think, do that on the same machine, but it may require some trickery.

Regardless of how you get two realms up and running, on the service side, what you are looking for is called "cross-realm authentication"


[http://www.faqs.org/faqs/kerberos-faq/general/section-48.html](http://www.faqs.org/faqs/kerberos-faq/general/section-48.html)

[http://web.mit.edu/Kerberos/krb5-1.5/krb5-1.5.4/doc/krb5-admin/Cross_002drealm-Authentication.html](http://web.mit.edu/Kerberos/krb5-1.5/krb5-1.5.4/doc/krb5-admin/Cross_002drealm-Authentication.html)

---

### Post by Lars Noodén on 2010-01-09
Thinking a bit more, I'm not sure I see a use-case for the cross-realm authentication here.  Would it not suffice to, once the user has authenticated in Kerberos, to look up group membership in LDAP and then let members of specific groups have access to the services in accordance with the level of access for that group?  One group for example.com, one group for db.example.com and one group for web.example.com, and so on...

---

