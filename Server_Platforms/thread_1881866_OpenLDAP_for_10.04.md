---
title: "OpenLDAP for 10.04"
date: 2011-11-16
forum: Server Platforms
---

### Post by HBED on 2011-11-16
Hello,
I'm a complete beginner with Ubuntu. I've been looking after a MS/Windows environment for about 10 years, but I have been asked to implement an Ubuntu network to a few of our sites. I have had some partial success with some of the elements (DHCP, Clonezilla, Static IP addresses etc.) I am now stuck on LDAP, or a method of user account creation/authentication.
Brief description of the requirement.
1 server (for DHCP/DNS/Small amount of file storage space)
Approx 30 PCs running Ubuntu desktop which users will need to be able to use their login to and access a shared folder.
This is an educational suite for a private company which might require a turnover of new user account creation/deletion on a weekly basis.
There are no other type of servers connected to this network.
 
I have worked through the document [here]("https://help.ubuntu.com/10.04/serverguide/C/openldap-server.html") for the initial installation. This works fine. But I don't want my domain to be called "example.com" I have tried substituting "example.com" for "mydomain.local". But, once I do this, I have the following error:
 
ldap_bind: Invlaid credentials (49)
 
I have not changed the password from the example ldif files which works fine before I attempt to change any of the domain informaiton.
 
As I said, I am a complete beginer at this, but I do have MS experience to try and draw on when it comes to making a comparison.
 
I would greatly appreciate any help if possible.
Many thanks
 
HBED

---

### Post by HBED on 2011-11-16
Hello again,
in addition to my post above, this is the content of the ldif files.

backend.example.com.ldif

# Load dynamic backend modules
dn: cn=module,cn=config
objectClass: olcModuleList
cn: module
olcModulepath: /usr/lib/ldap
olcModuleload: back_hdb

# Database settings
dn: olcDatabase=hdb,cn=config
objectClass: olcDatabaseConfig
objectClass: olcHdbConfig
olcDatabase: {1}hdb
olcSuffix: dc=winmarleigh,dc=local
olcDbDirectory: /var/lib/ldap
olcRootDN: cn=admin,dc=winmarleigh,dc=local
olcRootPW: secret
olcDbConfig: set_cachesize 0 2097152 0
olcDbConfig: set_lk_max_objects 1500
olcDbConfig: set_lk_max_locks 1500
olcDbConfig: set_lk_max_lockers 1500
olcDbIndex: objectClass eq
olcLastMod: TRUE
olcDbCheckpoint: 512 30
olcAccess: to attrs=userPassword by dn="cn=admin,dc=winmarleigh,dc=local" write by anonymous auth by self write by * none
olcAccess: to attrs=shadowLastChange by self write by * read
olcAccess: to dn.base="" by * read
olcAccess: to * by dn="cn=admin,dc=winmarleigh,dc=local" write by * read


and the other...

frontend.example.com.ldif

# Create top-level object in domain
dn: dc=winmarleigh,dc=local
objectClass: top
objectClass: dcObject
objectclass: organization
o: Example Organization
dc: Example
description: LDAP Example 

# Admin user.
dn: cn=admin,dc=winmarleigh,dc=local
objectClass: simpleSecurityObject
objectClass: organizationalRole
cn: admin
description: LDAP administrator
userPassword: secret

dn: ou=people,dc=winmarleigh,dc=local
objectClass: organizationalUnit
ou: people

dn: ou=groups,dc=winmarleigh,dc=local
objectClass: organizationalUnit
ou: groups

dn: uid=john,ou=people,dc=winmarleigh,dc=local
objectClass: inetOrgPerson
objectClass: posixAccount
objectClass: shadowAccount
uid: john
sn: Doe
givenName: John
cn: John Doe
displayName: John Doe
uidNumber: 1000
gidNumber: 10000
userPassword: password
gecos: John Doe
loginShell: /bin/bash
homeDirectory: /home/john
shadowExpire: -1
shadowFlag: 0
shadowWarning: 7
shadowMin: 8
shadowMax: 999999
shadowLastChange: 10877
mail: [email]john.doe@example.com[/email]
postalCode: 31000
l: Toulouse
o: Example
mobile: +33 (0)6 xx xx xx xx
homePhone: +33 (0)5 xx xx xx xx
title: System Administrator
postalAddress: 
initials: JD

dn: cn=example,ou=groups,dc=winmarleigh,dc=local
objectClass: posixGroup
cn: example
gidNumber: 10000


Thanks
HBED

---

### Post by luvshines on 2011-11-17
Hi

I don't know for sure since I have never tried the newer method of LDAP server configuration but the following> dn: dc=winmarleigh,dc=local
objectClass: top
objectClass: dcObject
objectclass: organization
o: Example Organization
[COLOR="Blue"]dc: Example[/COLOR]
description: LDAP Example looks to be problematic I guess

You have changed the dc in the DN for the top-level object but the dc in the stanza still read Example

---

### Post by HBED on 2011-11-17
Hi luvshines

Thanks so much for your response.  That makes sense.  I'm on leave at the moment so cant test it until i go back to the office.  I'll trywhen i get back on Monday and post to let you know how i get on.

Thanks once again
HBED

---

### Post by jaal on 2011-11-20
You want to install a domain?
 samba + ldap?
 if so you can follow this tutorial.

[http://tuxnetworks.blogspot.com/2010/07/howto-samba-ldap-on-1004-lucid-short.html](http://tuxnetworks.blogspot.com/2010/07/howto-samba-ldap-on-1004-lucid-short.html)

after installing samba + openldap, install LDAP Account Manager (LAM), and looking for a tutorial of LAM,
 from LAM can change everything, as the domain, user input, create groups etc ...

 samba + ldap authenticator domain is for computers running linux, win, mac, unix and you can make a replica pdc and bdc.

---

### Post by HBED on 2011-11-21
Hi jaal,
thanks for the link and the info.  In my absence, my colleague has made a little headway.  I did think about using Samba intially and still might, depending on how we get on with the rest of the server build.
 
In terms of the rest of the initial question, I will now resolve this thread, and when i find out how my colleague has got the issue working, i will post the solution which we used up for others to see and search on.

Thanks
HBED

---

### Post by HBED on 2011-11-21
Hi luvshines,
I've had a closer look at the revised script as you suggested, and indeed it was an omission on my part.  I changed the dc Example section and the script now works fine.
Thanks for your assitance.
HBED

---

