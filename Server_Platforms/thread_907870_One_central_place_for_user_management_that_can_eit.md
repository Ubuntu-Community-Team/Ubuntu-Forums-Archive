---
title: "One central place for user management that can either use or output to a SQL type DB"
date: 2008-09-01
forum: Server Platforms
---

### Post by nehsa on 2008-09-01
I had this posted in the general help section and it was suggested I post it here.

I've been researching different technologies for integrating all aspects of Linux into a central repository. Does anyone have any idea on this?

LDAP?

MySQL/PostgreSQL?

Radius?

What I want is really pretty simple. One place that I add a new user to the system. I want a user to login to the system and whatever technology authenticated him determine what services he has access to. (Radius/LDAP?)

OR

If a technology like this doesn't exist (or isn't flexible enough),  I would like to manually teach each service to refer to a SQL database when a user logs in (much more work probably).

The services I would like integrated are:

Direct shell access (Believe is using PAM now?)
SSH access
OpenVPN access
Samba Access
Docuwiki access
Mumble/Murmur access
Hula (maybe)

I think I could figure out how to create a useradd type script that includes the services above but then would have no idea how to teach the services to look at the database.  Using a technology like LDAP sounds like it may work but I need to ensure that the contents within it can be output freq. to a SQL type database.

My end goal is to create a web site that monitors all aspects of my server.  In the future I plan on adding more machines (gateway and DMZ) so this solution needs to be scalable.

Thanks for any feedback on this topic! I would also like to hear if there's a legitimate reason why Ubuntu is not already setup like this. Are there downsides I am not considering?

-Nehsa

---

### Post by nehsa on 2008-09-04
Anyone done anything like this?

---

