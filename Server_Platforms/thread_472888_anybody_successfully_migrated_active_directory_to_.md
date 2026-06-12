---
title: "anybody successfully migrated active directory to other LDAP(s)?"
date: 2007-06-13
forum: Server Platforms
---

### Post by netlogic on 2007-06-13
NT4 domain to Samba Domain is a snap, but I was wondering if someone had any success from migrating Active Directory to other LDAP (FREE) based system? 

Thanks again.

---

### Post by rickyjones on 2007-06-13
I've never actually done it before but I do know that you can export AD objects (like users) to a .CSV file. I'm assuming that there is a utility to bring info into openldap or similar from a .CSV file.

---

### Post by elst on 2007-06-13
> **rickyjones said:**
> I've never actually done it before but I do know that you can export AD objects (like users) to a .CSV file. I'm assuming that there is a utility to bring info into openldap or similar from a .CSV file.

You can treat AD as an LDAP v. 3 server and access the data through the appropriate library for your programming language (it was Perl in my case). IIRC, one potential interoperability issue is that the password hash formats are different, but I didn't need to deal with that data.

---

