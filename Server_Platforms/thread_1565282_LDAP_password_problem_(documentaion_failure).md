---
title: "LDAP password problem (documentaion failure?)"
date: 2010-08-31
forum: Server Platforms
---

### Post by gogHR on 2010-08-31
**edit: Sorry, but my search skills did not succeed at first, there is already a thread about this issue [here]("http://ubuntuforums.org/showthread.php?t=1487199").**

Hi,

I am trying to setup an LDAP server using the official documentation on [OpenLDAP server]("https://help.ubuntu.com/10.04/serverguide/C/openldap-server.html").

Everything goes fine until I try to view the ACL list with

```
**ldapsearch -xLLL -b cn=config -D cn=admin,cn=config -W olcDatabase=hdb olcAccess**
```and this is followed by "ldap_bind: Invalid credentials (49)" because the password I am entering is incorrect.

Is there a default password for cn=admin,cn=config? 

The only password that was set during the installation was for **[B]cn=admin,dc=example,dc=com**[/B] and It worked when I was adding frontend.example.com with this command:[B][B]

```
ldapadd -x -D cn=admin,dc=example,dc=com -W -f frontend.example.com.ldif
```[/B][/B]

Thank you for your help. I am new to LDAP, and as far as I can see, not using slapd.conf in the new versions of OpenLDAP is a major PITA.

Where should I report problems with the documentation?

---

