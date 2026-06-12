---
title: "Server guide for LDAP does not work"
date: 2009-09-11
forum: Server Platforms
---

### Post by Dave.Wynne on 2009-09-11
I've been trying for 5 days to set up a LDAP server.
I've thought perhaps it was an issue with my domain so I have installed the LDAP database as shown in the guide, and it still does not work.


1.3. Populating LDAP
The directory has been created during installation and reconfiguration, and now it is time to
populate it. It will be populated with a "classical" scheme that will be compatible with address book
applications and with Unix Posix accounts. Posix accounts will allow authentication to various
applications, such as web applications, email Mail Transfer Agent (MTA) applications, etc.
For external applications to authenticate using LDAP they will each need to be specifically
configured to do so. Refer to the individual application documentation for details.
LDAP directories can be populated with LDIF (LDAP Directory Interchange Format) files. Copy the
following example LDIF file, naming it example.com.ldif, somewhere on your system:
dn: ou=people,dc=example,dc=com
objectClass: organizationalUnit
ou: people
dn: ou=groups,dc=example,dc=com
objectClass: organizationalUnit
ou: groups
Network Authentication
55
dn: uid=john,ou=people,dc=example,dc=com
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
dn: cn=example,ou=groups,dc=example,dc=com
objectClass: posixGroup
cn: example
gidNumber: 10000

does not work!!!!

I've given up on that and so went to Samba
and...

4. Edit the generated /tmp/ldif_output/cn=config/cn=schema/cn={12}samba.ldif file,
changing the following attributes:
dn: cn=samba,cn=schema,cn=config
...
cn: samba
And remove the following lines from the bottom of the file:
structuralObjectClass: olcSchemaConfig
entryUUID: b53b75ca-083f-102d-9fff-2f64fd123c95
creatorsName: cn=config
createTimestamp: 20080827045234Z
entryCSN: 20080827045234.341425Z#000000#000#000000
modifiersName: cn=config
modifyTimestamp: 20080827045234Z
The attribute values will vary, just be sure the attributes are removed.
5. Finally, using the ldapadd utility, add the new schema to the directory:
ldapadd -x -D cn=admin,cn=config -W -f /tmp/ldif_output/cn\=config/cn\=schema/cn\=\{12\}samba.There should now be a dn: cn={X}misc,cn=schema,cn=config, where "X" is the next sequential
schema, entry in the cn=config tree.

Does not work


help me I'm going crazy.

Dave

---

### Post by Dave.Wynne on 2009-09-11
reboot fies all

---

