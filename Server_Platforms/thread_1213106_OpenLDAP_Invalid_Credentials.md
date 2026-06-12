---
title: "OpenLDAP Invalid Credentials"
date: 2009-07-14
forum: Server Platforms
---

### Post by black_wolf on 2009-07-14
I'm setting up a sever to do user authentication for a local domain following the Ubuntu 9.04 Server Guide: [https://help.ubuntu.com/9.04/serverguide/C/openldap-server.html]("https://help.ubuntu.com/9.04/serverguide/C/openldap-server.html"). Problem is that I'm using Ubuntu 9.04 Server, and the OpenLDAP package installed from the repos stores it's config file in the database rather than in the default file (which makes following other tutorials or directions difficult to say the least).

I can search the database fine with ldapsearch (so I know the password I'm using is correct), but whenever I try to add entries using ldapadd, I get this error:


> ldap_bind: Invalid credentials (49)


I've searched, but only found instances that want me to modify the slapd.conf file (which isn't being used), or is from user error. If user error is the case, please point out where I'm going wrong! 

Thanks

---

