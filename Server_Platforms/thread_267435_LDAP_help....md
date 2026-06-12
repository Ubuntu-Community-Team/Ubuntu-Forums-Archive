---
title: "LDAP help..."
date: 2006-09-28
forum: Server Platforms
---

### Post by oberon on 2006-09-28
I am trying to get phpldapadmin installed and working.  I tried using the pre-packaged out-of-date version in Universe, and I got errors when trying to login to it.  I thought it was just beacuse it wasn't liking PHP5 so I went downloaded directly for sorceforge.  I set up all the config files, yes I followed what is in the wiki, and ended up with the same issue.  It gives an error stating that it could not bind to the LDAP server (same error from both versions):
```

             Error
Could not bind to the LDAP server.

LDAP said: Undefined attribute type
Error number: 0x11 (LDAP_UNDEFINED_TYPE)
Description: The attribute type specified is invalid. 

```

I spent the last few hours digging through google search results and bug reports and have come up empty handed.  Any ideas would be very welcome. :) 

Thanks,

oberon

---

### Post by xlyz on 2006-10-06
same problem here. any suggestion wellcome :)

---

### Post by grahamw on 2006-10-19
Are you sure that you are using the format cn=admin,dc=example,dc=net for your login DN?

If you just use admin you will get this error.

---

