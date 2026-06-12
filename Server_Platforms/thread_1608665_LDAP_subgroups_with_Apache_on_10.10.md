---
title: "LDAP subgroups with Apache on 10.10"
date: 2010-10-29
forum: Server Platforms
---

### Post by RogueMolecule on 2010-10-29
Hi all,

I'm having some problems getting Apache to search LDAP subgroups. Otherwise LDAP authentication is working fine.

I'm using the standard authnz_ldap module as included with the stock Apache2 build.

'require ldap-group' works fine, but doesn't search any nested subgroups. When I add 'AuthLDAPMaxSubGroupDepth' as outlined here:

[http://httpd.apache.org/docs/trunk/mod/mod_authnz_ldap.html#authldapmaxsubgroupdepth](http://httpd.apache.org/docs/trunk/mod/mod_authnz_ldap.html#authldapmaxsubgroupdepth)

I get the following error:

Invalid command 'AuthLDAPMaxSubGroupDepth', perhaps misspelled or defined by a module not included in the server configuration
Action 'configtest' failed.

I assume it's because I'm using the included 'authnz_ldap' module as opposed to 'mod_authnz_ldap' module. Can anyone confirm that? Or are they the same thing? If they are, why is 'AuthLDAPMaxSubGroupDepth' not recognised?

If they are different, is there any way to force 'authnz_ldap' to search nested subgroups? Either that or do you know where I can download 'mod_authnz_ldap'? I can't find it anywhere.

Thanks in advance,

Don

---

### Post by Zefal on 2012-10-16
bump and I'd like to know this too!

---

### Post by Alekz_ on 2012-10-16
Are you sure authnz_ldap module is enable?

If so, you should read you apache logs. I'm pretty sure threre's something there that can point you the issue...

If you're not sure this module is enable, try to run

> a2enmod authnz_ldap

with root privilegies

---

