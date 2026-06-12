---
title: "How to add more rights to a group in openLDAP"
date: 2010-06-08
forum: Server Platforms
---

### Post by denarced on 2010-06-08
I have this group "cn=admins,ou=groups,dc=home,dc=com"
And I've configured slapd in the new way so I'm not using
slapd.conf (I think). First I thought about just modifying
the files at /etc/ldap/cn=config/.......
but that didn't work.
How do I make that group into an admin-group with all the 
rights ??

---

### Post by bjorgein on 2010-06-08
I'm not 100% sure but I think that the files in cn=config are just loaded when you first build the ldap server. You need to use ldapmodify to actually modify the database now that it has been loaded. As for adding admin rights, I think you can add rights by using the attribute olcAccess in the cn=config tree.

---

### Post by bjorgein on 2010-06-08
I actually just had a similar problem but I just fixed it.

Ran into the issue of insufficient access, the output was:
root@ldapTest:/etc/ldap/slapd.d# ldapadd -x -D 'cn=admin,dc=OMITTED,dc=com' -W -f /tmp/cn=samba.ldif
Enter LDAP Password: 
adding new entry "cn={12}samba,cn=schema,cn=config"
ldap_add: Insufficient access (50)

Solved it by adding the line "olcAccess: {0}to * by dn="cn=admin,dc=OMITTED,dc=com" write by * read" 
to the file olcDatabase={0}config.ldif which allows the admin account to modify anything.

I think you could easily add a similar line to give modification rights to an entire group.

---

### Post by denarced on 2010-06-08
> **bjorgein said:**
> I actually just had a similar problem but I just fixed it.

Ran into the issue of insufficient access, the output was:
root@ldapTest:/etc/ldap/slapd.d# ldapadd -x -D 'cn=admin,dc=OMITTED,dc=com' -W -f /tmp/cn=samba.ldif
Enter LDAP Password: 
adding new entry "cn={12}samba,cn=schema,cn=config"
ldap_add: Insufficient access (50)

Solved it by adding the line "olcAccess: {0}to * by dn="cn=admin,dc=OMITTED,dc=com" write by * read" 
to the file olcDatabase={0}config.ldif which allows the admin account to modify anything.

I think you could easily add a similar line to give modification rights to an entire group.

You'd think so yes. I tried modifying the line mentioned and there was something like 'olcAccess: {3}to * by group.exact="cn=admins,ou=groups,dc=some,dc=some" write'
It didn't give any error in the log files but members of the group didn't get any juice either.

---

