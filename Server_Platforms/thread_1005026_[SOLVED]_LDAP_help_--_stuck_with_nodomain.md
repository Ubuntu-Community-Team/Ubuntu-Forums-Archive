---
title: "[SOLVED] LDAP help -- stuck with nodomain"
date: 2008-12-07
forum: Server Platforms
---

### Post by troyready on 2008-12-07
Hello everyone! I'm new to the world of LDAP, and I've gotten completely stuck :confused:

So I've installed slapd and phpldapadmin (I read that it was good to use a gui ldap management tool for consistency), and done a "sudo dpkg-reconfigure slapd" to reconfigure it.

I put "exampleco.com" as my base DN, and "Example Company" as the organization name to use in the base DN. Database backend is HDB, and I selected to move the "old database files" out of the way (which I presume were left from the initial apt-get install).

This configuration succeeds, but things get weird when I log in with phpldapadmin:

The login page autodetects that my login should be "cn=admin,dc=nodomain". Strange, but not a big deal -  "cn=admin,dc=exampleco,dc=com" works as expected.

What I don't understand is why there is still a "nodomain" dc listed? (I've shown this in the attached picture).

Also, when I try to move it, copy it, add an attribute to it, or add a child entry, phpldapadmin always reports an error of 0x35 (LDAP_UNWILLING_TO_PERFORM).

Can anyone explain what I'm missing? I'm sure it's simple, but as I said, this is all new to me and I'm at a loss. Thanks in advance!

---

### Post by miller90 on 2008-12-15
Try with [LDAPSoft LDAP Browser]("http://www.ldapsoft.com/"), it is a free tool

or download and try [LDAP Admin Tool]("http://www.ldapsoft.com/ldapadmintool.html")

both works on ubuntu.

---

### Post by troyready on 2008-12-21
Interesting -- it does appear that the problem is with phpldapadmin, and not the ldap server itself.

Thank you very much for the reply; I'll try other options for administration.

---

### Post by troyready on 2008-12-21
Excellent -- upgrading to phpldapadmin 1.1.0.6 fixed the issue; I'd recommend everyone on 8.04 server avoid the repository version and get it directly from sf.net

---

### Post by paragkalra on 2009-09-20
This thread helped me solved my problem too...thanks Ubuntuforums....

---

### Post by djbon2112 on 2009-10-19
I just upgraded to 1.1.0.7 and it still seems broken... exact same error as OP. Suggestions? I need a web client.

---

