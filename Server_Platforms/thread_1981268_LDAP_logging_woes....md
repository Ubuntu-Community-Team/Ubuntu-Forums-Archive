---
title: "LDAP logging woes..."
date: 2012-05-16
forum: Server Platforms
---

### Post by lisanels47 on 2012-05-16
I get tons of logging in my logs now... I think it's because the following code enabled all of it.  Can someone show me how to change the logging to just show errors/failures?  Thanks!


Create the file logging.ldif with the following contents:

[I]dn: cn=config
changetype: modify
add: olcLogLevel
olcLogLevel: stats
Implement the change:[/I]

sudo ldapmodify -Q -Y EXTERNAL -H ldapi:/// -f *logging.ldif*

---

### Post by lisanels47 on 2012-05-20
Ok, fixed it.  Wasn't too hard, here's how:
Create the file logging.ldif with the following contents:

dn: cn=config
changetype: modify
**replace:** olcLogLevel
olcLogLevel: **none**

Implement the change:

sudo ldapmodify -Q -Y EXTERNAL -H ldapi:/// -f logging.ldif

---

