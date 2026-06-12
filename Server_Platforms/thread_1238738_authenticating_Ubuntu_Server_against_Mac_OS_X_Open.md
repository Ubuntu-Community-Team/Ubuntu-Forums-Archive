---
title: "authenticating Ubuntu Server against Mac OS X Open Directory"
date: 2009-08-12
forum: Server Platforms
---

### Post by dwhitese on 2009-08-12
Hello,

I have a few Ubuntu Server machines that I need to authenticate against OS X OD. I've done the usual dance with **auth-client-config** and so forth, and I can authenticate fine. Trouble comes, however, when I want to set up so that local root is an LDAP DB admin. I see a lot of this:

```
failed to bind to LDAP server ldap://---------------:389/: Invalid credentials
```The rootbinddn is set to (what I think is) a valid Open Directory administrator account and I can authenticate just fine without having a rootbinddn set (which tells me that the search base is valid). But when I set up a rootbinddn, stuff breaks. /etc/ldap.secret contains a valid password and is appropriately chmod'ded (0600). What am I missing?

FWIW, the rootbinddn entry in /etc/ldap.conf is:
```
rootbinddn cn=dbadmin,cn=users,dc=my,dc=ldap,dc=domain,dc=edu
```Thanks in advance.

---

### Post by muckst3r on 2009-11-13
I'm stuck in precisely the same spot. Anyone?

---

### Post by hewbert on 2011-07-10
I realize this is an ancient thread, but it's one of the top hits when Googling these keywords.

I'm not completely sure, but I'll bet the reason is because Open Directory doesn't store passwords in LDAP - Apple stores them in "Password Service."

I haven't done a lot of digging, but I don't know of any way to change OD passwords outside of Apple's native tools.

---

