---
title: "Kerberos and LDAP - Problem Loading Kerberos Schema"
date: 2013-02-08
forum: Server Platforms
---

### Post by kdiggs on 2013-02-08
Hi,
I am trying to build a [Kerberos and OpenLDAP]("https://help.ubuntu.com/12.04/serverguide/kerberos-ldap.html") server on Ubuntu 12.04.  I have completed the installation of the OpenLDAP system, as well as the SSL cert and the KDC configuration.  I am on the portion of the Kerberos and LDAP guide where I need to "add an index for the krb5principalname attribute" and I am having a problem.  I am receiving insufficient access messages when I enter my root dn and password. (note I am showing dc=example,dc=com but I omitting my actual info)
```
ldapmodify -x -D cn=admin,dc=example,dc=com -W
Enter LDAP Password: 
dn: olcDatabase={1}hdb,cn=config
add: olcDbIndex
olcDbIndex: krbPrincipalName eq,pres,sub

modifying entry "olcDatabase={1}hdb,cn=config"
ldap_modify: Insufficient access (50)

```
I cannot for the life of me figure out what I am doing wrong.  In the server guide they created a user called cn=admin,cn=config, but I am not sure I am required to do this or if I am, how to actually create that user.  Because I am able to successfully authenticate and I am not getting password error, I am thinking maybe it's a SASL issue?  Any help would be appreciated.  Thanks!

---

### Post by kdiggs on 2013-02-15
After continuous searching I finally found the answer.  For whatever reason, the creation of the user and ACL for cn=admin,cn=config was left off of the Ubuntu Server Network Authentication documentation.  Here's the main post I found:

```
http://serverfault.com/questions/171965/ubuntu-10-04-lucid-openldap-invalid-credentials-issue
```

First, create config.ldif with the following contents (changing the olcRootPW: secret to a unique password):

```
dn: olcDatabase={0}config,cn=config
changetype: modify
add: olcRootDN
olcRootDN: cn=admin,cn=config


dn: olcDatabase={0}config,cn=config
changetype: modify
add: olcRootPW
olcRootPW: secret


dn: olcDatabase={0}config,cn=config
changetype: modify
delete: olcAccess

```

Import the ldif file:
```
sudo ldapadd -Y EXTERNAL -H ldapi:/// -f config.ldif
```

Confirm the import worked:
```
ldapsearch -xLLL -b cn=config -D cn=admin,cn=config -W olcDatabase=hdb olcAccess
Enter LDAP Password: 
dn: olcDatabase={1}hdb,cn=config
olcAccess: {0}to attrs=userPassword,shadowLastChange,krbPrincipalKey by dn="cn
 =admin,dc=example,dc=com" write by anonymous auth by self write by * none
olcAccess: {1}to dn.base="" by * read
olcAccess: {2}to * by dn="cn=admin,dc=example,dc=com" write by * read
```

---

