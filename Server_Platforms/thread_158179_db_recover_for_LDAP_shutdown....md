---
title: "db_recover for LDAP shutdown..."
date: 2006-04-10
forum: Server Platforms
---

### Post by gertmul on 2006-04-10
My LDAP server unexpectedly powered down...and now no LDAP access...

"ldapsearch -x -D ...." results in: ldap_bind: Can't contact LDAP server (-1)

"slapd -d 8" results in:
=> bdb_last_id: get failed: Cannot allocate memory (12)
...
slapd stopped

Which, after time spend seems to me that a "db_recover" is needed...but which version and how do you use it? I tried db3-recover with no luck.

Please help.

---

### Post by gertmul on 2006-04-10
trial and error...for my 5.10 Breezy setup...

apt-get install db4.2-util
cd /var/lib/ldap
db4.2_dump anyfile.bdb   should give some data instead of version mismatch.
db4.2_recover -v 

/etc/init.d/slapd start

and 

ldapsearch -x -D ... working again! lost the last two entries, but who cares, Ubuntu rules!

---

