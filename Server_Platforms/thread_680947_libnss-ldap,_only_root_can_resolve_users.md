---
title: "libnss-ldap, only root can resolve users"
date: 2008-01-28
forum: Server Platforms
---

### Post by nocturn on 2008-01-28
I'm using libnss-ldap to resolve users on multiple systems.

Now, on the ldap server itself, the users only resolve as root.
Whe logging in, the user has the id 'i have no name'.  When nscd is used, they get their username again, but when doing id <user> as another user, it says the user does not exist...

I checked the filepermissions on every file and they are all world readable...

The server is running Ubuntu 6.06.2 server.

---

