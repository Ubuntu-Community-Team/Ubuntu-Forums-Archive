---
title: "LDAP Replication when schema unknown"
date: 2013-11-21
forum: Server Platforms
---

### Post by bobpaul on 2013-11-21
The previous "administrator" left behind an LDAP setup that's tied to a couple of nonessential services. Since he's left we've expanded it and have gotten to the point where it's now used by essential services and we're concerned by our lack of redundancy.

Unfortunately, following the [OpenLDAP Server page]("https://help.ubuntu.com/12.04/serverguide/openldap-server.html#openldap-server-replication") from the ubuntu documents hasn't gotten me very far. I seem to be getting stuck in Step 1 of the consumer setup "Make sure the slapd-config databse is identical to the Provider's. In particular, make sure schemas and the databse suffix are the same." If I proceed with the fresh install and continue through to the "Testing" section, I get the following result on both the provider and the consumer:

```
$ sudo ldapsearch -z1 -LLLQY EXTERNAL -H ldapi:/// -s base contextCSN
dn:

```

So think this is an issue with having a different schema on the provider than the consumer, but I don't know how to copy the schema over. What I have tried is exporting the entire ldap from the master with slapcat and importing with slapadd but then I just get different errors in syslog whenever replication is attempted.

```
slapd[20885]: syncrepl_message_to_entry: rid=006 mods check (objectClass: value #0 invalid per syntax)
```

When I start slapd on the consumer, I get the following errors in syslog:
```
Nov 21 18:38:58 marvel slapd[21021]: slapd starting
Nov 21 18:38:58 slave slapd[21021]: UNKNOWN attributeDescription "PWDFAILURETIME" inserted.
Nov 21 18:38:58 slave slapd[21021]: syncrepl_message_to_entry: rid=006 mods check (objectClass: value #0 invalid per syntax)
Nov 21 18:38:58 slave slapd[21021]: do_syncrepl: rid=006 rc 21 retrying
```

PWDFAILURETIME seems to be related to some password policy overlay that I don't think is functional or fully configured (we certainly don't seem to have any password policy restrictions).

What I think I need to do is copy just the schema from the master server to the slave (rather than doing the full slapcat | slapadd) but I'm not sure how to do that. Then it seems I also need to deal with this overlay (either removing it from the master or adding it to the slave) but I'm not sure how to identify even what it is or where it came from.

Can anyone point me in the right direction?

---

