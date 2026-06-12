---
title: "Samba Error When Joining Domain"
date: 2006-05-09
forum: Server Platforms
---

### Post by kozmo on 2006-05-09
When I issue the command:

**net rpc join member -U myusername**

I get the error message:

[B]Failed to open /var/lib/samba/secrets.tdb
utils/net_rpc.c:rpc_oldjoin_internals(266)
error storing domain sid for DOMAINNAME[/B]

The secrets.tdb file is present, so I don't why I get open it.

---

### Post by kozmo on 2006-05-09
The problem was a permissions issues.
As soon as I issued a CHMOD comand on the secrets.tdb file it worked.

---

### Post by LordHunter317 on 2006-05-09
You were running that command as root, right (or someone Samba sees as an admin user)?  You didn't open up screts.tdb to the world, right?  That would be real bad.

---

