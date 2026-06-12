---
title: "Quick LDAP Question"
date: 2010-08-16
forum: Server Platforms
---

### Post by TheSeanKelly on 2010-08-16
I'm trying to set up a centralized log-on scheme in a research lab with about 10 computers.  It's looking like we're going with LDAP - this decision may be out of my control (but if there's an alternative that would be REALLY better, do let me know)

My question is we don't really have a domain name, so when all the tutorials say cn=example,cn=com, I can't mimic this exactly.  I've been trying to get away with just one, like cn=researchlab.  Will LDAP work with just one, or do I need to invent a second also?

On the flipside, will it work with more?  Our server can be reached by lab.department.school.edu, could I do cn=lab,cn=department,cn=school,cn=edu?

I've never worked with LDAP and the tutorials I'm finding online are all over the place and pretty confusing.

Thanks for your help!

---

### Post by arrrghhh on 2010-08-16
I've never worked with LDAP either, but I know that you can create "test" domains within LDAP - so they don't have to be actual domains, just as long as on your LAN the domain exists.

Hopefully you haven't seen all these docs ;)

[OpenLDAP Server](https://help.ubuntu.com/community/OpenLDAPServer)
[LDAP Client Authentication](https://help.ubuntu.com/community/LDAPClientAuthentication)

Both of those are official Ubuntu documentation.  [This](http://ubuntuforums.org/showthread.php?t=361735) thread had some good information in it as well.  Post back if you're still having issues!

---

### Post by TheSeanKelly on 2010-08-16
> **arrrghhh said:**
> I've never worked with LDAP either, but I know that you can create "test" domains within LDAP - so they don't have to be actual domains, just as long as on your LAN the domain exists.

Hopefully you haven't seen all these docs ;)

[OpenLDAP Server](https://help.ubuntu.com/community/OpenLDAPServer)
[LDAP Client Authentication](https://help.ubuntu.com/community/LDAPClientAuthentication)

Both of those are official Ubuntu documentation.  [This](http://ubuntuforums.org/showthread.php?t=361735) thread had some good information in it as well.  Post back if you're still having issues!

Thanks for the help - I have seen those documents but they seem to be outdated - I've also seen a good number of people in arms about the documentation being incorrect.

It's a slow process - though I'm sure I'll get it together.

---

### Post by mtcycler on 2010-08-27
I have a similar question, we are in a school network and our url is of type dept.school.edu so the ldap dn: should be dn: dc=dept,dc=school,dc=edu but when we do that it rejects it as a "non-singular entry for single dc"

any ideas?

Thanks.

---

