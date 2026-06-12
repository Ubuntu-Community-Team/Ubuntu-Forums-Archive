---
title: "LDAP setting get overwriten"
date: 2006-08-20
forum: Server Platforms
---

### Post by dazedandconfused on 2006-08-20
Hi All,

I set up OpenLDAP on Dapper Server to run as an LDAP powered PDC for a Windows network. It all worked well until I ran:

apt-get install ubuntu-desktop 

at which point it downloaded all the packages for the desktop and then rather ominously announced that there was a problem with the slapd config which it then overwrote with the default.

Silly me, should have backed up all my hard work first but that's life ;)

Having been used to Mandriva I suppose I've got used to being asked if I want to stick with the old config during changes or upgrades so my question is how do I stop software that's already been configured from having its settings overwritten?

Cheers,

Jools

---

