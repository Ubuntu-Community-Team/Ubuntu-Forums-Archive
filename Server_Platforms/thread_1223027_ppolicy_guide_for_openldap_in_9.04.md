---
title: "ppolicy guide for openldap in 9.04?"
date: 2009-07-25
forum: Server Platforms
---

### Post by terencekent on 2009-07-25
Hello all,

I've been having quite a bit of trouble getting a working ppolicy setup using Ubuntu 9.04 server and openldap. All the guides for ppolicy that I've found are based around using the slapd.conf file, which isn't being used by default in the ubuntu packaged openldap*(2.4.15-1ubuntu3). I understand that I could just use a slapd.conf file by creating it by hand, but I'm trying to keep all the configuration in the 'recommended' cn=config tree.

 So here are my questions:

1. Does anybody know of a ppolicy guide using the cn=config method, instead of a slapd.conf file? Is it even possible?

2. If I can't use the cn=config route to setup ppolicy, can I create a slapd.conf file with *just* the ppolicy directives in it, and have ldap read the rest of the configuration from the cn=config tree?

Thanks in advance,
Terence.

---

### Post by DjMentat on 2011-01-17
[FONT=Times New Roman][SIZE=3]So I'm having the same issue here. I've spent a good month putting pieces of tutorials together to get OpenLDAP to work b/c there is no tutorial for the new version of OpenLDAP that installs as a package. Now that I finally have it up and running I need to configure the ppolicy overlay. I have converted the ppolicy.schema to a .ldif and added to my LDAP and confirmed that it is there, but where do I go from here when there is no slapd.conf file anymore? I have been searching for days and every tutorial and how to is for the older version of OpenLDAP that uses the slapd.conf file. [/SIZE][/FONT]
 
[FONT=Times New Roman][SIZE=3]I understand from my research that I'll need to edit a file to add the ppolicy overlay and then input the options below it, but what file do I need to edit and add the overlay to?[/SIZE][/FONT]
 
[FONT=Times New Roman][SIZE=3]Any help is apprcieated as I'm building a fully functional ubuntu network for a Linux Security class and I'm simply stuck at this point.[/SIZE][/FONT]
 
[FONT=Times New Roman][SIZE=3]Thanks,[/SIZE][/FONT]

---

### Post by alanrickman on 2011-05-12
Hi there!

I've had my LDAP server running for a few weeks now. All is running smoothly but I'm having absolutely no luck with the password policy overlay.

I have successfully imported the schema but I can find no way to define the default policy. Like both of the posts here I have no slapd.conf file so I'm unsure how to proceed.

Where can I configure ppolicy_default without the slapd.conf file?

If anyone can provide any hints they would be greatly appreciated!

Thanks!
Alan

---

