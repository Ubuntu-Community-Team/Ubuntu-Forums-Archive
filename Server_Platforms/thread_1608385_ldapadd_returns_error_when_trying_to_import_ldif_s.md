---
title: "ldapadd returns error when trying to import ldif schema"
date: 2010-10-29
forum: Server Platforms
---

### Post by densone on 2010-10-29
Hi, 
I am trying to import the following automount ldif and am getting the error below. Banging my head on this. Any help would be appreciated. 

**Ldif:**


dn: cn=schema
attributetypes: ( 1.3.6.1.4.1.2312.4.1.2 NAME 'automountInformation' DESC 'Information used by the autofs automounter' EQUALITY caseExactMatch SYNTAX 1.3.6.1.4.1.1466.115.121.1.26 SINGLE-VALUE )
objectclasses: ( 1.3.6.1.4.1.2312.4.2.3 NAME 'automount' SUP top STRUCTURAL DESC 'An entry in an automounter map' MUST ( cn $ automountInformation $ objectclass ) MAY ( description ) )
objectclasses: ( 1.3.6.1.4.1.2312.4.2.2 NAME 'automountMap' SUP top STRUCTURAL DESC 'An group of related automount objects' MUST ( ou ) )


**Error: **


host.com ~ # ldapadd -Y EXTERNAL -H ldapi:/// -f xx.ldif 
SASL/EXTERNAL authentication started
SASL username: gidNumber=0+uidNumber=0,cn=peercred,cn=external,cn=auth
SASL SSF: 0
adding new entry "cn=schema"
ldap_add: Invalid syntax (21)
	additional info: attributetypes: value #0 invalid per syntax

---

