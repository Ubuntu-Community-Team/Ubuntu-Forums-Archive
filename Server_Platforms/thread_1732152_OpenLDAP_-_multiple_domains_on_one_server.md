---
title: "OpenLDAP - multiple domains on one server?"
date: 2011-04-17
forum: Server Platforms
---

### Post by auphil on 2011-04-17
Hey Everybody,

I work for a college with many departments. I'd like to just deploy one LDAP/krb5 server (plus slave replicas) to authenticate all users in all departments.

Is it possible to do this?

Some of the DN formats would be:

dc=college,dc=university,dc=edu (the LDAP server lives here)

Departments:
dc=biology,dc=university,dc=edu
dc=chemistry,dc=university,dc=edu
dc=math,dc=university,dc=edu

Sample client machine FQDN names:

darwin.biology.university.edu
newton.math.university.edu
bohr.chemistry.university.edu

The proposed DNs for the departments matches what is done for NIS now.

If anyone has any pointers or URLs that describe how to properly do this, I'd really appreciate it.

Thanks,
Phil

---

### Post by headvampyre@hotmail.co.uk on 2011-04-22
Im not expert in this, but is this what your looking for?

[http://www.yolinux.com/TUTORIALS/LinuxTutorialLDAP-LDIF-example1.html](http://www.yolinux.com/TUTORIALS/LinuxTutorialLDAP-LDIF-example1.html)

---

