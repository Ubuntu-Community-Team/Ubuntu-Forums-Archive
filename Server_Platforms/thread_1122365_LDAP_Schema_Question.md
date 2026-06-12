---
title: "LDAP Schema Question"
date: 2009-04-11
forum: Server Platforms
---

### Post by Digitallogic on 2009-04-11
I have found plenty of resources/tutorials on installing OpenLDAP, and I have successfully configured my server (up and running and successfully authenticating).  My question relates to how I should setup the schema as I can not seem to find any useful resources on this.  I am also starting to think I am trying to make LDAP do more then it was intended to do so please feel free to point this out if that is the case.  Here is my scenario:

3 Servers with various LDAP capable applications on each (mostly web based)
3-5 classes of users (developers, interns, customers, managers, etc), each class of user requires access to a subset of all the applications

What I had thought to do is to assign each user to some 'role', and then grant application permission to the role rather then the user.  That way when I add new users I only have to assign them a role rather then access to individual applications.  Also that way if we added a new app or decided a class of users should have access to some existing application then it would only require updating the role rather then every user.

Is this some I can/should do with LDAP, or should I be looking at an alternative such as samba?

---

### Post by Digitallogic on 2009-04-14
Any thoughts?

---

### Post by francois.mdlh on 2009-04-17
> **Digitallogic said:**
> I have found plenty of resources/tutorials on installing OpenLDAP, and I have successfully configured my server (up and running and successfully authenticating).

Please let us all know how you managed to do that. Please.

---

### Post by Digitallogic on 2009-04-20
I used the [ubuntu ldap tutorial]("https://help.ubuntu.com/community/OpenLDAPServer").  It's pretty straight forward.

---

