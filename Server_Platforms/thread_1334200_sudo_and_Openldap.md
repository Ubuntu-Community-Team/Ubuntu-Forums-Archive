---
title: "sudo and Openldap"
date: 2009-11-22
forum: Server Platforms
---

### Post by PinkyTr4ffic on 2009-11-22
I've fully configured openldap with samba according to this tutorial.

[http://sanjaybdalal.wordpress.com/2009/06/23/setup-openldap-serversambaauto-mount-in-ubuntu-9-04/](http://sanjaybdalal.wordpress.com/2009/06/23/setup-openldap-serversambaauto-mount-in-ubuntu-9-04/)

Now i'm wondering if it's possible to give the ldap users root rights?

I've read the tutorials on how to move /etc/sudoers to the ldap server but in those tutorials they specify that you have to add the following line to your slapd.conf:

include /etc/ldap/schema/schema.openldap

This schema adds the sudo attributes to openldap.

My problem is now that i do not use slapd.conf and that i have to manually add all ldap schema's via ldapadd. Every time i try to add the schema it gives me an inexplicable error ==> error on line 1:""

Can someone help me ?

---

### Post by PinkyTr4ffic on 2009-11-22
bump !

---

### Post by PinkyTr4ffic on 2009-11-27
Bump !!!!!!!

---

### Post by beniwtv on 2009-11-27
You should not need to move /etc/sudoers (IMHO it's bad).

First make sure that PAM and NSS are correctly configured. Try to log-in to your server with a user in your LDAP tree (via SSH), and issue the command:

```
id
```

Make sure the user has the correct groups. At least, it should have the user's own group. To access sudo, the user also has to be in the group "admin". See the relevant sudoers entry:

```
# Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL

```

In your LDAP tree you should be able to add the different users to the admin group.

Cheers,

---

