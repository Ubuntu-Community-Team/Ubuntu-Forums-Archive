---
title: "Server 10.04 as an LDAP client of Active Directory?"
date: 2010-11-19
forum: Server Platforms
---

### Post by urbushey on 2010-11-19
(This was posted at the end of another thread, where it probably didn't belong, so reposting here)

I have Active Directory set up on one machine (and I can't really adjust the settings very much) and Ubuntu Server 10.04, which I would like to use as a client.

I followed the directions at [https://help.ubuntu.com/community/LDAPClientAuthentication](https://help.ubuntu.com/community/LDAPClientAuthentication), but when I get to 

```
getent passwd
``` 

I don't see anything from the LDAP, and ssh'ing into the box from an LDAP/AD username certainly doesn't work.

In addition, I've attempted to use [Webmin]("http://www.webmin.com/")'s LDAP Configuration module to configure it. I can connect to the server and can browse it with the LDAP browser with my settings, but the Webmin package doesn't recognize the users (which are organized in one of four Organizational Units (OUs) within the OU that I have as my Search Base) as users, i.e. it returns:

```

Searching for users ..
.. no users found under base OU=Office1,OU=All Offices,DC=mycompany,DC=com.

```

Does anyone have any suggestions? I'm not even sure which log files would be relevant.

---

### Post by urbushey on 2010-11-19
SOLVED!

I went to [https://help.ubuntu.com/8.04/serverguide/C/likewise-open.html](https://help.ubuntu.com/8.04/serverguide/C/likewise-open.html) and followed the direction for using Likewise Open there. Great success in about 4 cli commands.

---

