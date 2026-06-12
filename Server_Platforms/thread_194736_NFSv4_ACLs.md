---
title: "NFSv4 ACLs"
date: 2006-06-11
forum: Server Platforms
---

### Post by Soleil-Raid on 2006-06-11
After much waiting (for Dapper) and pushing and prodding, I've managed to get NFSv4 successfully working with full Kerberos authorization, and encryption of everything, which is great.

However, two items still cause me issues.
1) ACLs aren't exported over NFS. getfacl only shows the normal unix permission set, and setfacl complains that the operation isn't supported, despite the fact that ACLs are clearly working on the server.

2) NFSv4 looks for Kerberos CC files in the wrong place. If for example, user with uid 1000 stores it's credentials cache in /tmp/krb5cc_1000_S7Yzyb (where S7Yzyb is a psuedo random set of charchters), while the NFS client looks for the credentials cache in /tmp/krb5cc_1000.
This can be fixed by properly setting the KRB5CCNAME environment variable, although there's a plethora of places avaliable to do this. Since KRB5CCNAME is used by pam_krb5, it's not possible to stick this info in a home directory file without some ugly hacks. Therefore, the best way would seem to be to use /etc/environment, yet I can't get this to use the $UID value to set the filename properly, it continues to use set the name exactly - eg;
edward@mort ~ $ set|grep KRB5CCNAME
KRB5CCNAME='FILE:/tmp/krb5cc_${UID}'

Any thoughts?

---

