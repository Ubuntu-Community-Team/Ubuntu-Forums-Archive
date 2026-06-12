---
title: "ldapmodify ldap_bind invalid credentials with cn=config"
date: 2011-12-15
forum: Server Platforms
---

### Post by gillecaluim on 2011-12-15
[FONT=Arial][SIZE=1]I've installed slapd ....reinstalled and still getting the same errors while trying to add samba/ldap authentication.  Every time I try a ldapadd to add samba schema I get an error message ldap_bind: Invalid credentials (49).  
**ldapadd -x -D cn=admin,cn=config -W -f /tmp/cn=samba.ldif**[/SIZE][/FONT][FONT=Arial][SIZE=1] [/SIZE][/FONT][FONT=Arial][SIZE=1]
It seems the backend hdb rootPW isn't set to the same password as the frontend because I can't add entries.   The -x option should disable SASL authentication.  

I was able to add entry to cn=admin
**ldapadd -x -D cn=admin,dc=ourhome,dc=net -W -f /etc/ldap/frontend.ourhome.net.ldif**[/SIZE][/FONT][FONT=Arial][SIZE=1]
So any ideas why I can't modify cn=config with the normal credentials?

Robert[/SIZE][/FONT][FONT=Arial][SIZE=2] [/SIZE][/FONT][FONT=Arial][SIZE=4]:confused:[/SIZE][/FONT]

---

