---
title: "LDAP error: Invalid credentials(49) and insufficient access(50)"
date: 2012-01-14
forum: Server Platforms
---

### Post by hemartins on 2012-01-14
Hi,

I have a ubuntu server 11.10, and i'm trying to configuring Kerberos and LDAP using this tutorial: [https://help.ubuntu.com/11.10/serverguide/C/kerberos-ldap.html](https://help.ubuntu.com/11.10/serverguide/C/kerberos-ldap.html)

I have sucessfuly configured ldap and kerberos, but when I try to add kerberos schema to ldap:
```
ldapadd -x -D cn=admin,cn=config -W -f /tmp/cn\=kerberos.ldif
Enter LDAP Password:
ldap_bind: Invalid credentials(49)
```

It's strange because i have sure that the password it's correct, and if i try with cn=admin only, it works, but in ldapmodify commands it returns: insufficient access(50=.

I have googled a lot to search for a solution to my problem, but so far no solution worked where.

Any sugestions?

regards,
Henrique Marints

---

### Post by hemartins on 2012-01-18
anyone??

---

### Post by Cladd on 2012-02-28
I had this same error, and it may be too late to help you, hemartins, but I was able to finish adding the schema using the instructions on adding a schema on the OpenLDAP install tutorial here: [https://help.ubuntu.com/11.10/serverguide/C/openldap-server.html](https://help.ubuntu.com/11.10/serverguide/C/openldap-server.html)

This is the command I used, adapted for the kerberos tutorial:

sudo ldapadd -Q -Y EXTERNAL -H ldapi:/// -f /tmp/cn\=kerberos.ldif

Afterward, I used this command in replace of the ldapmodify commands in the later steps (typing or copying/pasting in the bold text from the wiki):

sudo ldapmodify -Q -Y EXTERNAL -H ldapi:///

---

