---
title: "Ldap: taming the 'host' attribute"
date: 2007-08-03
forum: Server Platforms
---

### Post by WheelDweller on 2007-08-03
Like a lot of people, I have a working LDAP instance that lets me authenticate people locally. And I'm using phpldapadmin to feel my way through what I can add, and what I can't. It seems to know.

The goal is to add the "host" attribute, so pam_ldap can check for it on each machine, limiting the user to a finite set of machines.

I understand adding an "auxilliary" structure, and then claiming it to be 'host', I can pull this off.  But has anyone actually _done_ it?

Every time I get to people who know the fix, they explain it in ways that don't fit into my head for very long, like DIT, DN, ObjectClass and such....maybe I'm just tired...or too old for this sort of thing...:(

Thanks

---

