---
title: "LDAP Error"
date: 2007-07-09
forum: Server Platforms
---

### Post by chrisdeeley on 2007-07-09
I'm trying to setup an LDAP server, using SLAPD, and using webmin to administer it remotely.

Everything work's fine until I try to add a new user in webmin's LDAP User & Group's utility. I get the error message:

Failed to save user : Failed to add user to LDAP database : no structuralObjectClass operational attribute

I don't understand why it won't add user's, but add's group's fine. 

Has anyone seen this error before, and know how to correct it?

Thank you in advance.

---

### Post by wildphins on 2007-09-30
I was curious if you ever solved this problem.  I am learning Linux and trying to get LDAP running.  I really like the Webmin interface but am having the same problem.  Any help you can provide would be great.  Thanks!

---

### Post by gpredrag on 2007-10-01
I don't know what exactly is webadmin trying to do, but this error suggests that template for user account, as set in your webadmin is missing structural object class.
Objects in LDAP have ObjectClass attribute (to distinguish what exactly that object represents: user, group, IPhost, automount information, etc.) Every object must have one structural object class (which is sufficient to create an object) and zero or more auxiliary object classes (which are not sufficient to create an object but provide additional attributes).
Somewhere in webmin configuration there must be "blueprint" which objectclasses represent "user account", and that "blueprint" is missing structural object classess.

---

### Post by chrisdeeley on 2007-10-01
> **wildphins said:**
> I was curious if you ever solved this problem.  I am learning Linux and trying to get LDAP running.  I really like the Webmin interface but am having the same problem.  Any help you can provide would be great.  Thanks!

WILDPHINS, 

The way I solved the problem was in webmin, go to LDAP Users & Groups and click on module config. In the first section *LDAP Server Options*, select YES for *Show fields for given name and surname*.

The problem I was having was that SLAPD seems to require that you enter a value for these before it will create the entry.

Best of luck!

---

### Post by wildphins on 2007-10-01
Thanks! That actually helps quite a bit, in combination with further testing that I have done.

---

### Post by micheld on 2007-12-08
hi there, guess i'm a bit late, but anyways for reference, here we go:

background:
-had the same issue
-found this entry
-reproduced issue

solution (on my system at least with webmin_1.380_all.deb):
-select module config for LDAP Users and Groups 
-tick YES for  "Show fields for given name and surname?" as per above post
-add "posixAccount" to "Object class to add for given name?" field

---

