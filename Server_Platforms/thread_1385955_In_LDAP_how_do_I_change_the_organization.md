---
title: "In LDAP how do I change the organization"
date: 2010-01-20
forum: Server Platforms
---

### Post by lil_elvis2000 on 2010-01-20
I've got 8.10 of Ubuntu and currently running openLDAP and have SAMBA domain using this along with the PAM changes on all machines to authenticate the logins.

Now I've got a situation where I need to change the organization it currently is dc=mycomp, dc=local and I need to change the "local" part.

I thought that I could slapcat it out then change all dc=local to dc=blech and then reload the LDAP database.   Then go around and change all the ldap configuration points to match.

I don't think its as simple as change the base dn and everything below that will update...or am I wrong.

How would I best go about this?
Thanks.

---

### Post by lil_elvis2000 on 2010-01-29
It does not look like this is possible, easily. I think I need to create a second DB, I've no idea if that will work. and then loadup the ldif file from slapcat of the current DB.

Have tried slapadd - but gives an error. So perhaps OpenLDAP can only handle a single DB with a single olcSuffix?

---

