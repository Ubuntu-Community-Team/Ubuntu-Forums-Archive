---
title: "ldap+samba+ubuntu 10.04"
date: 2010-06-04
forum: Server Platforms
---

### Post by richardsith on 2010-06-04
Hi guys,
I need a support to configure a LDAP Server with authentication by Samba on Ubuntu 10.04.

I've followed these how-to presented on these links

[http://doc.ubuntu.com/ubuntu/serverguide/C/openldap-server.html]("http://doc.ubuntu.com/ubuntu/serverguide/C/openldap-server.html")
and
[http://doc.ubuntu.com/ubuntu/serverguide/C/samba-ldap.html]("http://doc.ubuntu.com/ubuntu/serverguide/C/samba-ldap.html")

for the first one I've not problems of configuration, the problem is on second one when I use this command

**ldapadd -x -D cn=admin,cn=config -W -f /tmp/cn\=samba.ldif**

I receive the following error

[B]Enter LDAP Password:
ldap_bind: Invalid credentials (49)[/B]

I've also changed the command with this one 

**ldapadd -x -D cn=admin,dc=ideaglu,dc=net -W -f /tmp/cn\=samba.ldif**

[B]Enter LDAP Password:
adding new entry "cn=samba,cn=schema,cn=config"
ldap_add: Insufficient access (50)[/B]

the error is different but adding the new entry.
I don't know where the mistake is.

Someone could help me? please

thanks in advance.

---

### Post by richardsith on 2010-06-05
is there anyone that can help me?

---

### Post by MMoudry on 2010-06-05
I have the same problem... although I managed to insert it with
sudo ldapadd -Y EXTERNAL -H ldapi:/// -f /tmp/cn\=samba.ldif

also do NOT change the line dn: cn=samba,cn=schema,cn=config to dn: cn=samba

I am still stuck on creating indexes for samba at the moment


Also this might help, not sure though :
[http://www.opinsys.fi/setting-up-openldap-on-ubuntu-10-04-alpha-2-lucid-part-3](http://www.opinsys.fi/setting-up-openldap-on-ubuntu-10-04-alpha-2-lucid-part-3)

---

### Post by cynicl12000 on 2010-06-06
> **MMoudry said:**
> I have the same problem... although I managed to insert it with
sudo ldapadd -Y EXTERNAL -H ldapi:/// -f /tmp/cn\=samba.ldif

also do NOT change the line dn: cn=samba,cn=schema,cn=config to dn: cn=samba

Thanks, helped a ton!

I got the indexes loaded using a similar method:

The indexes appear to have loaded with:

sudo ldapmodify -Y EXTERNAL -H ldapi:/// -f samba_indexes.ldif

but I'm fairly new to *nix and may have screwed it up.  The output was:

> SASL/EXTERNAL authentication started
SASL username: gidNumber=0+uidNumber=0,cn=peercred,cn=external,cn=auth
SASL SSF: 0
modifying entry "olcDatabase={1}hdb,cn=config"

---

### Post by MMoudry on 2010-06-06
ok I managed to hack around the index creation problems for samba as well and get it all working.

1. Generate the cn\=samba.ldif file. Remove the bottom lines as specified in the guide. DO NOT change the top line.
2. As root copy the cn\=samba.ldif to /etc/ldap/schema/samba.ldif
3. Make sure you use a clean LDAP install and execute : sudo ls /etc/ldap/schema/*.ldif | xargs -I {} sudo ldapadd -Y EXTERNAL -H ldapi:/// -f {}
- This will insert all schemas with .ldif extension from /etc/ldap/schema
4. Insert the samba indexes into your backend.example.com.ldif filethat is specified in the server guide, right beside the other indexes. This avoids using the cn=admin,cn=config authentication
5. Import the backend.example.com.ldif with : sudo ldapadd -Y EXTERNAL -H ldapi:/// -f backend.example.com.ldif
6. Follow the rest of the guide


If anyone wishes more info post here pls

---

### Post by richardsith on 2010-06-06
thanks for your help,

I explain you the procedure that I made, following then what you told us.

before to get the hands on the OpenLDAP's files I run these commands

**sudo apt-get install samba samba-doc**

[B]sudo cp /usr/share/doc/samba-doc/examples/LDAP/samba.schema.gz /etc/ldap/schema/
[/B]
[B]sudo gzip -d /etc/ldap/schema/samba.schema.gz
[/B]
**sudo nano schema_convert.conf**

adding these lines
```

include /etc/ldap/schema/core.schema
include /etc/ldap/schema/collective.schema
include /etc/ldap/schema/corba.schema
include /etc/ldap/schema/cosine.schema
include /etc/ldap/schema/duaconf.schema
include /etc/ldap/schema/dyngroup.schema
include /etc/ldap/schema/inetorgperson.schema
include /etc/ldap/schema/java.schema
include /etc/ldap/schema/misc.schema
include /etc/ldap/schema/nis.schema
include /etc/ldap/schema/openldap.schema
include /etc/ldap/schema/ppolicy.schema
include /etc/ldap/schema/samba.schema
```


**mkdir /tmp/ldif_output**

**slapcat -f schema_convert.conf -F /tmp/ldif_output -n0 -s "cn={12}samba,cn=schema,cn=config" > /tmp/cn=samba.ldif**

remove the lines 

```
structuralObjectClass: olcSchemaConfig
entryUUID: b53b75ca-083f-102d-9fff-2f64fd123c95
creatorsName: cn=config
createTimestamp: 20080827045234Z
entryCSN: 20080827045234.341425Z#000000#000#000000
modifiersName: cn=config
modifyTimestamp: 20080827045234Z
```

**sudo cp /tmp/cn\=samba.ldif /etc/ldap/schema/samba.ldif**


when I run the command 

**sudo ls /etc/ldap/schema/*.ldif | xargs -I {} sudo ldapadd -Y EXTERNAL -H ldapi:/// -f {}**


the result is 

```
SASL/EXTERNAL authentication started
SASL username: gidNumber=0+uidNumber=0,cn=peercred,cn=external,cn=auth
SASL SSF: 0
adding new entry "cn=core,cn=schema,cn=config"
ldap_add: Other (e.g., implementation specific) error (80)
	additional info: olcAttributeTypes: Duplicate attributeType: "2.5.4.2"

SASL/EXTERNAL authentication started
SASL username: gidNumber=0+uidNumber=0,cn=peercred,cn=external,cn=auth
SASL SSF: 0
adding new entry "cn=cosine,cn=schema,cn=config"

SASL/EXTERNAL authentication started
SASL username: gidNumber=0+uidNumber=0,cn=peercred,cn=external,cn=auth
SASL SSF: 0
adding new entry "cn=inetorgperson,cn=schema,cn=config"

SASL/EXTERNAL authentication started
SASL username: gidNumber=0+uidNumber=0,cn=peercred,cn=external,cn=auth
SASL SSF: 0
adding new entry "cn=misc,cn=schema,cn=config"

SASL/EXTERNAL authentication started
SASL username: gidNumber=0+uidNumber=0,cn=peercred,cn=external,cn=auth
SASL SSF: 0
adding new entry "cn=nis,cn=schema,cn=config"

SASL/EXTERNAL authentication started
SASL username: gidNumber=0+uidNumber=0,cn=peercred,cn=external,cn=auth
SASL SSF: 0
adding new entry "cn=openldap,cn=schema,cn=config"

SASL/EXTERNAL authentication started
SASL username: gidNumber=0+uidNumber=0,cn=peercred,cn=external,cn=auth
SASL SSF: 0
adding new entry "cn=samba,cn=schema,cn=config"
```


if you look the screen at the top of it there is a error (80)

then I followed the guide made in this way

**nano db.test.net.ldif**

```
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
olcSuffix: dc=test,dc=net
olcDbDirectory: /var/lib/ldap
olcRootDN: cn=admin,dc=test,dc=net
olcRootPW: admin
olcDbConfig: set_cachesize 0 2097152 0
olcDbConfig: set_lk_max_objects 1500
olcDbConfig: set_lk_max_locks 1500
olcDbConfig: set_lk_max_lockers 1500
olcDbIndex: objectClass eq
olcLastMod: TRUE
olcDbCheckpoint: 512 30
olcAccess: to attrs=userPassword by dn="cn=admin,dc=test,dc=net" write by anonymous auth by self write by * none
olcAccess: to attrs=shadowLastChange by self write by * read
olcAccess: to dn.base="" by * read
olcAccess: to * by dn="cn=admin,dc=test,dc=net" write by * read
```


**sudo ldapadd -Y EXTERNAL -H ldapi:/// -f db.test.net.ldif**

------------------------------------------------------------

[B]sudo nano users.test.net.ldif[

```
# Create top-level object in domain
dn: dc=test,dc=net
objectClass: top
objectClass: dcObject
objectclass: organization
o: test.net
dc: test
description: test Network

# Admin User
dn: cn=admin,dc=test,dc=net
objectClass: simpleSecurityObject
objectClass: organizationalRole
cn: admin
description: LDAP administrator
userPassword: admin

dn: ou=users,dc=test,dc=net
objectClass: organizationalUnit
ou: users

dn: ou=groups,dc=test,dc=net
objectClass: organizationalUnit
ou: groups

# Ric Mag User
dn: uid=ricmag,ou=users,dc=test,dc=net
objectClass: inetOrgPerson
objectClass: posixAccount
objectClass: shadowAccount
uid: ricmag
sn: Mag
givenName: Ric
cn: Ric Mag
displayName: Ric Mag
uidNumber: 1010
gidNumber: 10000
userPassword: ricmag
gecos: Ric Mag
loginShell: /bin/bash
homeDirectory: /home/ricmag
shadowExpire: -1
shadowFlag: 0
shadowWarning: 7
shadowMin: 8
shadowMax: 999999
shadowLastChange: 10877
mail: [email]ricmag@test.net[/email]
postalCode: 67051
l: Avezzano
o: test.net
mobile: +33 (0)6 xx xx xx xx
homePhone: +33 (0)5 xx xx xx xx
title: System User
postalAddress:
initials: RM

dn: cn=office,ou=groups,dc=test,dc=net
objectClass: posixGroup
cn: office
gidNumber: 10000
```


**sudo ldapadd -x -D cn=admin,dc=ideaglu,dc=net -W -f users.test.net.ldif**


For the rest of the procedure as you saw I've no received any errors, just that one. Could you help me to resolve that,please

---

### Post by MMoudry on 2010-06-06
Hello,
The error you are experiencing is normal. The command I gave you lists all the files with .ldif extension from the directory and attempts to insert each of them into the LDAP database. The CORE schema is already inserted by default so the error just means that he cannot insert it again. From the procedure you described your database is clean and you've initialized the slapd correctly.

Mipam

---

### Post by richardsith on 2010-06-06
I've tried to continue to go on with the guide but on step after that I've received the error:

[COLOR="DarkOrchid"]
ldap_bind: Invalid credentials (49)[/COLOR]
 
like the first post. The command I used is

**sudo ldapmodify -x -D cn=admin,cn=config -W -f samba_indexes.ldif**

as reported on the guide. 

It's just my opinion, but it's strange that are present wrong steps on a official guide, isn't it?

---

### Post by MMoudry on 2010-06-07
> **cynicl12000 said:**
> 
I got the indexes loaded using a similar method:

The indexes appear to have loaded with:

sudo ldapmodify -Y EXTERNAL -H ldapi:/// -f samba_indexes.ldif


cynic got it working as depicted in the post above.

The problem is the access method using : -D cn=admin,cn=config

My guess would be that this 'community' supported guide wasn't updated yet to reflect changes in 10.04.

Mipam

---

### Post by richardsith on 2010-06-07
so,
and now what do I've to do? waiting the upgrade of the guide or ..........
 trying to make the same step previously made, so move the file samba_indexes.ldif in  /etc/ldap/schema/

and then relaunch the command

sudo ls /etc/ldap/schema/*.ldif | xargs -I {} sudo ldapadd -Y EXTERNAL -H ldapi:/// -f {}

?????

---

### Post by MMoudry on 2010-06-07
well you can put the indexes into your db.test.net.ldif. 

1. Just follow your procedure that you posted here from the beginning.
2. During the step where you create the 'nano db.test.net.ldif' put the samba index lines in there as follows :
```

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
olcSuffix: dc=test,dc=net
olcDbDirectory: /var/lib/ldap
olcRootDN: cn=admin,dc=test,dc=net
olcRootPW: admin
olcDbConfig: set_cachesize 0 2097152 0
olcDbConfig: set_lk_max_objects 1500
olcDbConfig: set_lk_max_locks 1500
olcDbConfig: set_lk_max_lockers 1500
olcDbIndex: objectClass eq

# SOME OTHER USEFUL INDEXES PUT BY MMOUDRY
olcDbIndex: uid pres,eq
olcDbIndex: cn,sn,mail pres,eq,approx,sub
# END SOME OTHER USEFUL INDEXES PUT BY MMOUDRY

# SAMBA INDEXES
olcDbIndex: uidNumber eq
olcDbIndex: gidNumber eq
olcDbIndex: loginShell eq
olcDbIndex: memberUid eq,pres,sub
olcDbIndex: uniqueMember eq,pres
olcDbIndex: sambaSID eq
olcDbIndex: sambaPrimaryGroupSID eq
olcDbIndex: sambaGroupType eq
olcDbIndex: sambaSIDList eq
olcDbIndex: sambaDomainName eq
olcDbIndex: default sub
# END SAMBA INDEXES

olcLastMod: TRUE
olcDbCheckpoint: 512 30
olcAccess: to attrs=userPassword by dn="cn=admin,dc=test,dc=net" write by anonymous auth by self write by * none
olcAccess: to attrs=shadowLastChange by self write by * read
olcAccess: to dn.base="" by * read
olcAccess: to * by dn="cn=admin,dc=test,dc=net" write by * read


```

3. After that just follow the rest of your procedure as you have written.

Mipam

---

### Post by richardsith on 2010-06-11
hello MMoudry,
thanks for your cooperation, I've added the lines that you've suggested me and I repeated all steps until this

ldapmodify -x -D cn=admin,cn=config -W -f samba_indexes.ldif

as reportered from the guide ([https://help.ubuntu.com/10.04/serverguide/C/samba-ldap.html](https://help.ubuntu.com/10.04/serverguide/C/samba-ldap.html)).
I've also try to change that one with this one

ldapmodify -x -D cn=admin,dc=ideaglu,dc=net -W -f samba_indexes.ldif 

but the error rest the same 

modifying entry "olcDatabase={1}hdb,cn=config"
ldap_modify: Insufficient access (50)


it's my think but there is somethings wrong on the guide [https://help.ubuntu.com/10.04/serverguide/C/samba-ldap.html](https://help.ubuntu.com/10.04/serverguide/C/samba-ldap.html), the installation of Ldap and its own configuration ([https://help.ubuntu.com/10.04/serverguide/C/openldap-server.html](https://help.ubuntu.com/10.04/serverguide/C/openldap-server.html)) doesn't give me any errors.

---

### Post by MMoudry on 2010-06-11
All right let's try this again.... Here is your procedure. I have modified it to reflect the samba index changes. Please follow it to the letter on a clean ldap install and it will import your indexes.... Because the indexes are already in one of the files you **DON'T** need to do the last step of 'ldapmodify -x -D cn=admin,cn=config -W -f samba_indexes.ldif'.



sudo apt-get install samba samba-doc

sudo cp /usr/share/doc/samba-doc/examples/LDAP/samba.schema.gz /etc/ldap/schema/

sudo gzip -d /etc/ldap/schema/samba.schema.gz

sudo nano schema_convert.conf

adding these lines
Code:

```

include /etc/ldap/schema/core.schema
include /etc/ldap/schema/collective.schema
include /etc/ldap/schema/corba.schema
include /etc/ldap/schema/cosine.schema
include /etc/ldap/schema/duaconf.schema
include /etc/ldap/schema/dyngroup.schema
include /etc/ldap/schema/inetorgperson.schema
include /etc/ldap/schema/java.schema
include /etc/ldap/schema/misc.schema
include /etc/ldap/schema/nis.schema
include /etc/ldap/schema/openldap.schema
include /etc/ldap/schema/ppolicy.schema
include /etc/ldap/schema/samba.schema

```

mkdir /tmp/ldif_output

slapcat -f schema_convert.conf -F /tmp/ldif_output -n0 -s "cn={12}samba,cn=schema,cn=config" > /tmp/cn=samba.ldif

remove the lines

Code:
```

structuralObjectClass: olcSchemaConfig
entryUUID: b53b75ca-083f-102d-9fff-2f64fd123c95
creatorsName: cn=config
createTimestamp: 20080827045234Z
entryCSN: 20080827045234.341425Z#000000#000#000000
modifiersName: cn=config
modifyTimestamp: 20080827045234Z

```

sudo cp /tmp/cn\=samba.ldif /etc/ldap/schema/samba.ldif


when I run the command

sudo ls /etc/ldap/schema/*.ldif | xargs -I {} sudo ldapadd -Y EXTERNAL -H ldapi:/// -f {}


the result is

Code:
```

SASL/EXTERNAL authentication started
SASL username: gidNumber=0+uidNumber=0,cn=peercred,cn=external,cn=auth
SASL SSF: 0
adding new entry "cn=core,cn=schema,cn=config"
ldap_add: Other (e.g., implementation specific) error (80)
	additional info: olcAttributeTypes: Duplicate attributeType: "2.5.4.2"

SASL/EXTERNAL authentication started
SASL username: gidNumber=0+uidNumber=0,cn=peercred,cn=external,cn=auth
SASL SSF: 0
adding new entry "cn=cosine,cn=schema,cn=config"

SASL/EXTERNAL authentication started
SASL username: gidNumber=0+uidNumber=0,cn=peercred,cn=external,cn=auth
SASL SSF: 0
adding new entry "cn=inetorgperson,cn=schema,cn=config"

SASL/EXTERNAL authentication started
SASL username: gidNumber=0+uidNumber=0,cn=peercred,cn=external,cn=auth
SASL SSF: 0
adding new entry "cn=misc,cn=schema,cn=config"

SASL/EXTERNAL authentication started
SASL username: gidNumber=0+uidNumber=0,cn=peercred,cn=external,cn=auth
SASL SSF: 0
adding new entry "cn=nis,cn=schema,cn=config"

SASL/EXTERNAL authentication started
SASL username: gidNumber=0+uidNumber=0,cn=peercred,cn=external,cn=auth
SASL SSF: 0
adding new entry "cn=openldap,cn=schema,cn=config"

SASL/EXTERNAL authentication started
SASL username: gidNumber=0+uidNumber=0,cn=peercred,cn=external,cn=auth
SASL SSF: 0
adding new entry "cn=samba,cn=schema,cn=config"

```

if you look the screen at the top of it there is a error (80)

then I followed the guide made in this way

nano db.test.net.ldif

Code:
```

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
olcSuffix: dc=test,dc=net
olcDbDirectory: /var/lib/ldap
olcRootDN: cn=admin,dc=test,dc=net
olcRootPW: admin
olcDbConfig: set_cachesize 0 2097152 0
olcDbConfig: set_lk_max_objects 1500
olcDbConfig: set_lk_max_locks 1500
olcDbConfig: set_lk_max_lockers 1500
olcDbIndex: objectClass eq

# SOME OTHER USEFUL INDEXES PUT BY MMOUDRY
olcDbIndex: uid pres,eq
olcDbIndex: cn,sn,mail pres,eq,approx,sub
# END SOME OTHER USEFUL INDEXES PUT BY MMOUDRY

# SAMBA INDEXES
olcDbIndex: uidNumber eq
olcDbIndex: gidNumber eq
olcDbIndex: loginShell eq
olcDbIndex: memberUid eq,pres,sub
olcDbIndex: uniqueMember eq,pres
olcDbIndex: sambaSID eq
olcDbIndex: sambaPrimaryGroupSID eq
olcDbIndex: sambaGroupType eq
olcDbIndex: sambaSIDList eq
olcDbIndex: sambaDomainName eq
olcDbIndex: default sub
# END SAMBA INDEXES

olcLastMod: TRUE
olcDbCheckpoint: 512 30
olcAccess: to attrs=userPassword by dn="cn=admin,dc=test,dc=net" write by anonymous auth by self write by * none
olcAccess: to attrs=shadowLastChange by self write by * read
olcAccess: to dn.base="" by * read
olcAccess: to * by dn="cn=admin,dc=test,dc=net" write by * read

```

sudo ldapadd -Y EXTERNAL -H ldapi:/// -f db.test.net.ldif

------------------------------------------------------------

[B]sudo nano users.test.net.ldif[

Code:
```

# Create top-level object in domain
dn: dc=test,dc=net
objectClass: top
objectClass: dcObject
objectclass: organization
o: test.net
dc: test
description: test Network

# Admin User
dn: cn=admin,dc=test,dc=net
objectClass: simpleSecurityObject
objectClass: organizationalRole
cn: admin
description: LDAP administrator
userPassword: admin

dn: ou=users,dc=test,dc=net
objectClass: organizationalUnit
ou: users

dn: ou=groups,dc=test,dc=net
objectClass: organizationalUnit
ou: groups

# Ric Mag User
dn: uid=ricmag,ou=users,dc=test,dc=net
objectClass: inetOrgPerson
objectClass: posixAccount
objectClass: shadowAccount
uid: ricmag
sn: Mag
givenName: Ric
cn: Ric Mag
displayName: Ric Mag
uidNumber: 1010
gidNumber: 10000
userPassword: ricmag
gecos: Ric Mag
loginShell: /bin/bash
homeDirectory: /home/ricmag
shadowExpire: -1
shadowFlag: 0
shadowWarning: 7
shadowMin: 8
shadowMax: 999999
shadowLastChange: 10877
mail: ricmag@test.net
postalCode: 67051
l: Avezzano
o: test.net
mobile: +33 (0)6 xx xx xx xx
homePhone: +33 (0)5 xx xx xx xx
title: System User
postalAddress:
initials: RM

dn: cn=office,ou=groups,dc=test,dc=net
objectClass: posixGroup
cn: office
gidNumber: 10000

```

sudo ldapadd -x -D cn=admin,dc=ideaglu,dc=net -W -f users.test.net.ldif

---

### Post by richardsith on 2010-06-11
Until here everything is right, now I've understood...you inserted the following lines 

olcDbIndex: uidNumber eq
olcDbIndex: gidNumber eq
olcDbIndex: loginShell eq
olcDbIndex: uid eq,pres,sub
olcDbIndex: memberUid eq,pres,sub
olcDbIndex: uniqueMember eq,pres
olcDbIndex: sambaSID eq
olcDbIndex: sambaPrimaryGroupSID eq
olcDbIndex: sambaGroupType eq
olcDbIndex: sambaSIDList eq
olcDbIndex: sambaDomainName eq
olcDbIndex: default sub

in the file db.test.net.ldif, in this way it's not necessary make that steps. I'll try to go head with the guide and I'll inform you if will have problems,
For now thanks a lot

---

### Post by richardsith on 2010-06-21
hi MMoudry,

in this days I've had a bit time to remake all procedure about it without received any errors, until here. Continuing the guide 

[https://help.ubuntu.com/10.04/serverguide/C/samba-ldap.html](https://help.ubuntu.com/10.04/serverguide/C/samba-ldap.html)

I've run the following commands

sudo perl /usr/share/doc/smbldap-tools/configure.pl

[B]$# is no longer supported at /usr/share/doc/smbldap-tools/configure.pl line 314.
-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-
       smbldap-tools script configuration
       -=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=
Before starting, check
 . if your samba controller is up and running.
 . if the domain SID is defined (you can get it with the 'net getlocalsid')

 . you can leave the configuration using the Crtl-c key combination
 . empty value can be set with the "." character
-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-
Looking for configuration files...

Samba Configuration File Path [/etc/samba/smb.conf] > 

The default directory in which the smbldap configuration files are stored is shown.
If you need to change this, enter the full directory path, then press enter to continue.
Smbldap-tools Configuration Directory Path [/etc/smbldap-tools/] > 
-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=
Let's start configuring the smbldap-tools scripts ...

. workgroup name: name of the domain Samba act as a PDC
  workgroup name [WORKGROUP] > 
. netbios name: netbios name of the samba controler
  netbios name [] > Ubuntu
. logon drive: local path to which the home directory will be connected (for NT Workstations). Ex: 'H:'
  logon drive [] > 
. logon home: home directory location (for Win95/98 or NT Workstation).
  (use %U as username) Ex:'\\Ubuntu\%U'
  logon home (press the "." character if you don't want homeDirectory) [\\Ubuntu\%U] > 
. logon path: directory where roaming profiles are stored. Ex:'\\Ubuntu\profiles\%U'
  logon path (press the "." character if you don't want roaming profile) [\\Ubuntu\profiles\%U] > 
. home directory prefix (use %U as username) [/home/%U] > 
. default users' homeDirectory mode [700] > 
. default user netlogon script (use %U as username) [] > %U
  default password validation time (time in days) [45] > 
. ldap suffix [] > dc=test,dc=net
. ldap group suffix [] > ou=groups
. ldap user suffix [] > ou=users
. ldap machine suffix [] > 
. Idmap suffix [ou=Idmap] > 
. sambaUnixIdPooldn: object where you want to store the next uidNumber
  and gidNumber available for new users and groups
  sambaUnixIdPooldn object (relative to ${suffix}) [sambaDomainName=WORKGROUP] > 
[COLOR="Red"]Use of uninitialized value $server in substitution (s///) at /usr/share/doc/smbldap-tools/configure.pl line 244, <STDIN> line 17.
. ldap master server: IP adress or DNS name of the master (writable) ldap server
Use of uninitialized value $example_value in concatenation (.) or string at /usr/share/doc/smbldap-tools/configure.pl line 161, <STDIN> line 17.
Use of uninitialized value $example_value in string at /usr/share/doc/smbldap-tools/configure.pl line 162, <STDIN> line 17.[/COLOR]
  ldap master server [] > 192.168.0.14
. ldap master port [389] > 
. ldap master bind dn [] > cn=admin,dc=test,dc=net
. ldap master bind password [] > 
. ldap slave server: IP adress or DNS name of the slave ldap server: can also be the master one
Use of uninitialized value $server in string at /usr/share/doc/smbldap-tools/configure.pl line 262, <STDIN> line 21.
  ldap slave server [] > 
. ldap slave port [389] > 
. ldap slave bind dn [] > 
. ldap slave bind password [] >   Warning: You really need to set this parameter...
  ldap slave bind password [] > 
. ldap tls support (1/0) [0] > 
. SID for domain WORKGROUP: SID of the domain (can be obtained with 'net getlocalsid Ubuntu')
  SID for domain WORKGROUP [S-1-5-21-3795947541-4050598190-2468368243] > 
. unix password encryption: encryption used for unix passwords
  unix password encryption (CRYPT, MD5, SMD5, SSHA, SHA) [SSHA] > 
. default user gidNumber [513] > 
. default computer gidNumber [515] > 
. default login shell [/bin/bash] > 
. default skeleton directory [/etc/skel] > 
. default domain name to append to mail adress [] > ideaglu.net
-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=
[COLOR="Red"]Use of uninitialized value $# in concatenation (.) or string at /usr/share/doc/smbldap-tools/configure.pl line 314, <STDIN> line 34.[/COLOR]
backup old configuration files:
  /etc/smbldap-tools/smbldap.conf->/etc/smbldap-tools/smbldap.conf.old
  /etc/smbldap-tools/smbldap_bind.conf->/etc/smbldap-tools/smbldap_bind.conf.old
writing new configuration file:
  /etc/smbldap-tools/smbldap.conf done.
  /etc/smbldap-tools/smbldap_bind.conf done.[/B]


then

**[COLOR="SlateGray"]sudo slapcat -l backup.ldif[/COLOR]**

and using the command 

**[COLOR="SlateGray"]sudo smbldap-populate[/COLOR]**

received that

[B][COLOR="Red"]Populating LDAP directory for domain WORKGROUP (S-1-5-21-3795947541-4050598190-2468368243)
(using builtin directory structure)

Use of uninitialized value $config{"suffix"} in pattern match (m//) at /usr/sbin/smbldap-populate line 141.
Use of uninitialized value $config{"suffix"} in concatenation (.) or string at /usr/sbin/smbldap-populate line 149.
can't extract first attr and value from suffix  at /usr/sbin/smbldap-populate line 149.[/COLOR][/B]

do you know what it means the red lines, please? 

thanks a lot

---

### Post by nutznboltz on 2010-09-30
schema2ldif script:

```

#! /bin/bash

# schema2ldif - convert foo.schema to foo.ldif

schema_name=$1

TEMPDIR=`mktemp -d`

trap "rm -r $TEMPDIR" 0 1 2 3

index_num=$(slapcat -f schema_convert.conf -F $TEMPDIR -n 0 | grep ${schema_name}, | sed -e 's/^.*{/{/' -e 's/}.*$/}/' )

slapcat -f schema_convert.conf -F $TEMPDIR -n0 -s cn=${index_num}${schema_name},cn=schema,cn=config | \
  sed -e "s/^dn: cn=${index_num}/dn: cn=/" -e "s/^cn: ${index_num}/cn: /" -e '/^structuralObjectClass: olcSchemaConfig/,$d'
```

requires a schema_convert.conf
example:
```
include /etc/ldap/schema/core.schema
include /etc/ldap/schema/collective.schema
include /etc/ldap/schema/corba.schema
include /etc/ldap/schema/cosine.schema
include /etc/ldap/schema/autofs.schema
include /etc/ldap/schema/duaconf.schema
include /etc/ldap/schema/dyngroup.schema
include /etc/ldap/schema/inetorgperson.schema
include /etc/ldap/schema/java.schema
include /etc/ldap/schema/ldapns.schema
include /etc/ldap/schema/misc.schema
include /etc/ldap/schema/nis.schema
include /etc/ldap/schema/authldap.schema
include /etc/ldap/schema/openldap.schema
include /etc/ldap/schema/pmi.schema
include /etc/ldap/schema/ppolicy.schema
include /etc/ldap/schema/samba.schema
include /etc/ldap/schema/solaris.schema
include /etc/ldap/schema/sudo.schema
```

Sample usage:

1) fetch autofs schema
```

mkdir autofs-schema
cd autofs-schema
apt-get source autofs
sudo cp autofs*/samples/autofs.schema /etc/ldap/schema/
cd ..
```

2) convert it
```

./schema2ldif autofs > autofs.ldif
```

---

### Post by nutznboltz on 2010-09-30
Bug report requesting that the script in the previous post be added to the documentation:

[https://bugs.launchpad.net/ubuntu/+source/ubuntu-docs/+bug/652448](https://bugs.launchpad.net/ubuntu/+source/ubuntu-docs/+bug/652448)

---

### Post by pav5088 on 2010-10-04
I tried to make some potential improvement to the above script ie. gave
it the ability to build its own .conf.  The only problem is the modified
script now needs knowledge about schema deps...  at the moment I only have
an incomplete hand-built dep config - it would be great if someone could
automate generation of all schema deps for schemas in /etc/ldap/schema .
This would be the last piece to make the tool completely userfriendly.

My not-quite-improvements can be found here :
[https://oss.gonicus.de/labs/gosa-contrib/browser/squeeze-install-scripts/trunk](https://oss.gonicus.de/labs/gosa-contrib/browser/squeeze-install-scripts/trunk)

---

