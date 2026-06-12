---
title: "Problem with LDAP"
date: 2012-03-20
forum: Server Platforms
---

### Post by Tres_Iqus on 2012-03-20
I have problems integrating Kerberos to my server (Domain Controller Samba and Ldap) that is working properly. following the guidance of Kerberos Ldap:

**ldapmodify -x -D cn=admin,cn=config -W** Enter LDAP Password:
**ldap_bind: Invalid credentials (49)** 
throws me this error and I can not continue the setup


I want to make Kerberos SSO mode

Ubuntu server 10.04LTS
Services:
LDAP
Samba
Kerberos


in advance Best regards, if I can fix this

---

### Post by Tres_Iqus on 2012-03-20
will try to configure kerberos with the command

 sudo ldapmodify-Q-Y EXTERNAL-H ldapi :/ / /-f cn = kerberos.ldif

---

### Post by hawkmage on 2012-03-20
Are you sure about your DN in your first post? You have two "cn" elements in it, I have never seen an LDAP Distinguished name with more than 1 Common Name in it.

---

### Post by Tres_Iqus on 2012-03-20
is in the ubuntu server guide from the official website [https://help.ubuntu.com/10.04/serverguide/C/kerberos-ldap.html](https://help.ubuntu.com/10.04/serverguide/C/kerberos-ldap.html) n° 5 

then as it should be time for the modification?

---

