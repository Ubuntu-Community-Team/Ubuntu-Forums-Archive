---
title: "Samba LDAP Shared Accounts"
date: 2008-10-07
forum: Server Platforms
---

### Post by khalis on 2008-10-07
I spent a little time looking for a solution on my own, but to no avail.  Since its a probably simple question, I'll just ask away.

I'm using Samba3 and OpenLDAP to serve my samba shares and domain, but I have a local user on the server (khalis) that I want to add to the LDAP database without losing the local account on the server.  I want the user's home directory available as a home share on the samba server, but khalis' password still stored in /etc/passwd in case the ldap server ever goes down.

This seems to be similar to how LDAP maps root to the server.  Any help is appreciated.

---

### Post by erwall on 2008-10-07
> **khalis said:**
> I spent a little time looking for a solution on my own, but to no avail.  Since its a probably simple question, I'll just ask away.

I'm using Samba3 and OpenLDAP to serve my samba shares and domain, but I have a local user on the server (khalis) that I want to add to the LDAP database without losing the local account on the server.  I want the user's home directory available as a home share on the samba server, but khalis' password still stored in /etc/passwd in case the ldap server ever goes down.

This seems to be similar to how LDAP maps root to the server.  Any help is appreciated.
In this case, don't add the user to ldap, just add it in samba.  You should be able to just

```
smbpasswd khalis
```

and it should work as you want it to.

---

### Post by khalis on 2008-10-07
That does what I was hoping for, just a quick follow-up question:

Where does it store that user information?  Just out of curiosity.

---

### Post by erwall on 2008-10-07
> **khalis said:**
> That does what I was hoping for, just a quick follow-up question:

Where does it store that user information?  Just out of curiosity.
usually in /var/lib/samba/secrets.tdb

---

