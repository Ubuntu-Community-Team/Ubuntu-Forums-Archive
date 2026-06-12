---
title: "Beginner ldap question - dc?"
date: 2007-08-14
forum: Server Platforms
---

### Post by s0n|k on 2007-08-14
I've got openldap installed and running. I now need to submit some ldif files. Is there a nice graphical tool for this? I'm using GQ as a browser, but I can't really create ldif files with it. 

Anyway, let's take this example:

dn: dc=companyname,dc=com
dc: companyname
objectClass: dcObject
objectClass: organizationalUnit
ou: Companyname Dot Com

dn: ou=employees,dc=companyname,dc=com
ou: employees
objectClass: organizationalUnit 

I understand virtually everything except the dc.

I see how it works here, but my domain is multi levels deep. For example, how would you write 'mail.messages.yahoo.com' for the dc? I've tried a few things but keep getting a "cn is not present in entry". For the dn im doing this: dc=mail,dc=messages, etc... and that seems to be working fine.

---

### Post by koenn on 2007-08-14
> **s0n|k said:**
>  keep getting a "cn is not present in entry".

apparently the record / object you're creating requires a cn (canonical name ?) attribute. Try something like

```
dn : cn=mail,dc=messages, dc=yahoo,dc=com
cn: mail
```
or something along those lines. The exact syntax depends on the Directory Schema (i think), and I have no idea what that looks like.

---

