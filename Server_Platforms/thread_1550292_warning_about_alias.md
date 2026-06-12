---
title: "warning about alias"
date: 2010-08-10
forum: Server Platforms
---

### Post by associates on 2010-08-10
Hi,

I was wondering if I could get some help with the following error messages when trying to re-start the apache2 on Ubuntu Server 10.04

[warn] The Alias directive in /etc/squirrelmail/apache.conf at line 1 will probably never match because it overlaps an earlier Alias. [warn] The Alias directive in /etc/phpldapadmin/apache.conf at line 3 will probably never match because it overlaps an earlier Alias.
...waiting [warn] The Alias directive in /etc/squirrelmail/apache.conf at line 1 will probably never match because it overlaps an earlier Alias. [warn] The Alias directive in /etc/phpldapadmin/apache.conf at line 3 will probably never match because it overlaps an earlier Alias.
[OK]

I wonder if anyone might be able to tell me what i should do to fix this warnings.

Any help would be greatly appreciated.

Thank you in advance

---

### Post by Ryan Dwyer on 2010-08-11
It means the same alias was defined previously in both cases, so there's a double up. Did you manually add alias directives to your Apache config after installing squirrelmail and phpldapadmin? Because if you did, you didn't need to.

Find where in the config (probably /etc/apache2/apache2.conf) the directives were previously defined and remove them.

---

