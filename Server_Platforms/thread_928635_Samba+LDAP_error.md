---
title: "Samba+LDAP error"
date: 2008-09-24
forum: Server Platforms
---

### Post by g-dux on 2008-09-24
Setting up Samba+LDAP PDC. Can anyone tell me what this means and how to fix it?

Sep 24 07:25:49 server slapd[11894]: <= bdb_equality_candidates: (uid) not indexed 
Sep 24 07:27:19 server slapd[11894]: <= bdb_equality_candidates: (uid) not indexed 
Sep 24 07:27:51 server slapd[11894]: <= bdb_equality_candidates: (uid) not indexed 
Sep 24 07:28:35 server slapd[11894]: conn=2098 op=4 do_add: invalid dn (sambaDomainName=WORKGROUP,dc=ehg,dc=net) 
Sep 24 07:28:35 server slapd[11894]: <= bdb_equality_candidates: (uid) not indexed 
root@server:~# 


I think the error is the WORKGROUP entry but when I comment it out of SMB.CONF it still occurs.

Thanks in advance.

---

