---
title: "LDAP sudoers in an existing LDAP schema"
date: 2013-06-14
forum: Server Platforms
---

### Post by gregg_hughes on 2013-06-14
Good afternoon, all!

I'm starting to integrate some Ubuntu 12.04 servers into our datacenters and have one hurdle I haven't managed to overcome.

We have an existing OpenLDAP schema, with an existing OU with Administrators in it.  I want to set up sudo_ldap to allow LDAP users in that Administrators OU to have sudoers privilege without modifying sudoers on each server.  I've dragged the marshes and swamps for documentation and how-to for this situation, but have come up empty-handed.

Is there a way to set up sudo_ldap to simply grant the Administrator user special magical powers if they're in the Administrators OU?

Thanks to all for considering this!

---

### Post by Cheesemill on 2013-06-14
I don't use LDAP myself but try taking a read through this page, it may point you in the right direction.

[http://www.danbishop.org/2012/06/02/ubuntu-12-04-ultimate-server-guide/](http://www.danbishop.org/2012/06/02/ubuntu-12-04-ultimate-server-guide/)

---

