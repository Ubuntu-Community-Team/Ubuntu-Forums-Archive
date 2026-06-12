---
title: "FreeRadius and Ldap on Ubuntu 10.04"
date: 2011-05-17
forum: Server Platforms
---

### Post by ryazkhan on 2011-05-17
LDAP and FreeRadius they both are know as beasts when it comes to setting them up and configuring them properly. But once you got them they are piece of cake going forward.

I am using both of them since Ubuntu 8.04, but in Ubuntu 10.04 thing has been changed in every aspects, newer versions, different configs etc are some of those changes.

But I got both of them with 10.04 very long time ago but my setup back then were with samba, but this time I have configured them without samba so it just LDAP and FreeRadius. I thought maybe my pain will be gain for someone

Enough talking, lets get to work.
I am assuming that you already have Ubuntu 10.04 [server/desktop] with ssh [not required tho] up and running
I am also assuming that you have setup the static IP for your machine, not required though but good idea
The domain name/tree name we will be using in this examples is > dc=myldap,dc=ent
The basic group which will hold our user accounts is > cn=Domain Users,ou=Groups,dc=myldap,dc=ent
The users will be in Users OU > ou=Users,dc=myldap,dc=ent
Feel free to change any of the above according to you setup So lets start

Be root instead of typing password everytime you use sudo
> sudo bash
Check update and install if needed
> apt-get update && apt-get upgrade
Install slapd and its utils
> sudo apt-get install slapd ldap-utils -y
Add basic schemas in ldap database
> sudo ldapadd -Y EXTERNAL -H ldapi:/// -f /etc/ldap/schema/cosine.ldif
sudo ldapadd -Y EXTERNAL -H ldapi:/// -f /etc/ldap/schema/nis.ldif
sudo ldapadd -Y EXTERNAL -H ldapi:/// -f /etc/ldap/schema/inetorgperson.ldif
Setup core
> nano /tmp/mysetup.ldif
And paste the following in it, feel free to change the tree name
> # Load dynamic backend modules
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
olcSuffix: dc=myldap,dc=ent
olcDbDirectory: /var/lib/ldap
olcRootDN: cn=admin,dc=myldap,dc=ent
olcRootPW: mypassword
olcDbConfig: set_cachesize 0 2097152 0
olcDbConfig: set_lk_max_objects 1500
olcDbConfig: set_lk_max_locks 1500
olcDbConfig: set_lk_max_lockers 1500
olcDbIndex: objectClass eq
olcLastMod: TRUE
olcDbCheckpoint: 512 30
olcAccess: to attrs=userPassword by dn="cn=admin,dc=myldap,dc=ent" write by anonymous auth by self write by * none
olcAccess: to attrs=shadowLastChange by self write by * read
olcAccess: to dn.base="" by * read
olcAccess: to * by dn="cn=admin,dc=myldap,dc=ent" write by * read
Add the above ldif file
> sudo ldapadd -Y EXTERNAL -H ldapi:/// -f /tmp/mysetup.ldif
Setup ldap for authentication
> sudo apt-get --yes install ldap-auth-client
You will be asked few question, answer them very carefully and after reading.
LDAP server in this case is local host so it would ldap://127.0.0.1/
DN would be dc=myldap,dc=ent
Accept Version 3 as default
Answer Yes to next question
Answer No to next question
Ldap root account would be cn=admin,dc=myldap,dc=ent
And ldap root[admin in this case] password would be mypassword

Check setup
> sudo auth-client-config -t nss -p lac_ldap There should not be any error at this point, if there is then something is not right 
Update pam for ldap authentication
> sudo pam-auth-update ldap Make sure ldap is selected at least
Edit ldap.conf to adjust authentication option
> nano /etc/ldap.conf
Uncomment line 24
Uncomment line 72 and replace hard with soft
Save the file and exit out of it
Copy this file to /etc/ldap/ directory
> cp /etc/ldap/ldap.conf /etc/ldap/ldap.old
cp /etc/ldap.conf /etc/ldap/
Make home directory where user profiles will be places
> mkdir /ldaphome
chmod 777 /ldaphome
Setup basic groups and users
> nano /tmp/myldap.ldif
And paste the following in it
> # Create top-level object in domain
dn: dc=myldap,dc=ent
objectClass: top
objectClass: dcObject
objectclass: organization
o: Ldap Enterprise
dc: MYLDAP
description: LDAP Enterprise

# Admin user.
dn: cn=admin,dc=myldap,dc=ent
objectClass: simpleSecurityObject
objectClass: organizationalRole
cn: admin
description: LDAP administrator
userPassword: mypassword

dn: ou=Groups,dc=myldap,dc=ent
objectClass: organizationalUnit
ou: Groups

dn: cn=Domain Users,ou=Groups,dc=myldap,dc=ent
objectClass: posixGroup
objectClass: top
cn: Domain Users
gidNumber: 513
description: Domain Users

dn: ou=Users,dc=myldap,dc=ent
objectClass: organizationalUnit
ou: Users

dn: uid=rkhan,ou=Users,dc=myldap,dc=ent
objectClass: organizationalPerson
objectClass: person
objectClass: top
objectClass: posixAccount
objectClass: shadowAccount
uid: rkhan
sn: Khan
cn: Ryaz Khan
uidNumber: 30000
gidNumber: 513
userPassword: test
gecos: Ryaz Khan
loginShell: /bin/bash
homeDirectory: /ldaphome/rkhan
shadowExpire: -1
shadowFlag: 0
shadowWarning: 7
shadowMin: 8
shadowMax: 999999
shadowLastChange: 10877
title: System Administrator
Now add the above ldif file/basic structure to ldap database
> sudo ldapadd -x -D cn=admin,dc=myldap,dc=ent -w mypassword -f /tmp/myldap.ldif
This should run without any error, if there is/are, something is not right
At this point you should be able to login to your system with user rkhan
You might get error about the home directory does not exists while doing ssh, you can create it manually or if you are using desktop, login with rkhan and it will create the directory. But this is not a show stopper any shape or form
Now lets move to our next setup [freeradius], lets install and setup this monster
> apt-get install freeradius freeradius-ldap -y
Copy the openldap schema needed for freeradius to work to ldap schema directory
> cp /usr/share/doc/freeradius/examples/openldap.schema /etc/ldap/schema/
Convert the above schema you just copied to ldif file so it can be added to ldap database
> nano /tmp/schema_convert.ldif
And paste the following, delete any existing entries from the file, if there is any
> include /etc/ldap/schema/core.schema
include /etc/ldap/schema/corba.schema
include /etc/ldap/schema/cosine.schema
include /etc/ldap/schema/dyngroup.schema
include /etc/ldap/schema/inetorgperson.schema
include /etc/ldap/schema/misc.schema
include /etc/ldap/schema/nis.schema
include /etc/ldap/schema/openldap.schema
Create ldif file for openldap schema
> slapcat -f /tmp/schema_convert.ldif -F ~ -n0 -s "cn={7}openldap,cn=schema,cn=config" > /tmp/cn=openldap.ldif
Clean the above ldif file a bit
> nano /tmp/cn\=openldap.ldif
Remove number and {} from first lines to make it like the following
> dn: cn=openldap,cn=schema,cn=config
...
cn: openldap
And get rid of following lines, there is no use of these but they will/can cause trouble, they are located at the end of openldap.ldif
> structuralObjectClass: olcSchemaConfig
entryUUID: c69d2a24-1274-1030-8c56-69db9ca637cf
creatorsName: cn=config
createTimestamp: 20110514125231Z
entryCSN: 20110514125231.473294Z#000000#000#000000
modifiersName: cn=config
modifyTimestamp: 20110514125231Z
Now just add the above cleaned ldif file to ldap database
> sudo ldapadd -Y EXTERNAL -H ldapi:/// -f /tmp/cn\=openldap.ldif Again there should not be any error
To make sure the schemas we have added so far are in place, issue the following
> sudo ldapsearch -LLL -Y EXTERNAL -H ldapi:/// -b cn=config dn You will get list of all schemas
Now ldap server is ready with frad schema, its time to configure it
I would simply restart both monster [ldap and freeradius] just to be safe, not required though
> service slapd restart
service freeradius restart
Back to configuration
> nano /etc/freeradius/modules/ldap
You want to make sure that at least followings are in place, rest of the file is good by default for out setup
> server = "localhost"
identity = "cn=admin,dc=myldap,dc=ent"
password = mypassword
basedn = "ou=Users,dc=myldap,dc=ent"
filter = "(uid=%{%{Stripped-User-Name}:-%{User-Name}})"
base_filter = "(objectclass=radiusprofile)"
access_attr = "dialupAccess"
password_attribute = userPassword
Tell freeradius to use ldap for authentication by edit the following file
> nano /etc/freeradius/sites-enabled/default
Uncomment ldap, located on line 170, 181, and 182
Also tell freeradius to use ldap within tunnel as well, otherwise it simply would not work and you will damage your head by hitting it against the wall
> nano /etc/freeradius/sites-enabled/inner-tunnel
Uncomment line 129 (ldap)
We are pretty much done, so restart both monster [ldap and freeradius]
> service slapd restart
service freeradius restart
Issue the following command to see that ldap mapping is working correctely
> freeradius -XXX
If something like following is in place, we are good here, everything is working the way it designed
> Sat May 14 09:12:39 2011 : Debug: rlm_ldap: Registering ldap_groupcmp for Ldap-Group
Debug: rlm_ldap: Registering ldap_xlat with xlat_name ldap
Debug: rlm_ldap: LDAP radiusCheckItem mapped to RADIUS $GENERIC$
Debug: rlm_ldap: LDAP radiusReplyItem mapped to RADIUS $GENERIC$
Debug: rlm_ldap: LDAP radiusAuthType mapped to RADIUS Auth-Type
Debug: rlm_ldap: LDAP lmPassword mapped to RADIUS LM-Password
Debug: rlm_ldap: LDAP ntPassword mapped to RADIUS NT-Password
Debug: rlm_ldap: LDAP sambaLmPassword mapped to RADIUS LM-Password
Debug: rlm_ldap: LDAP sambaNtPassword mapped to RADIUS NT-Password
Debug: rlm_ldap: LDAP dBCSPwd mapped to RADIUS LM-Password
Debug: rlm_ldap: LDAP acctFlags mapped to RADIUS SMB-Account-CTRL-TEXT
Debug: rlm_ldap: LDAP radiusExpiration mapped to RADIUS Expiration
Debug: rlm_ldap: LDAP radiusNASIpAddress mapped to RADIUS NAS-IP-Address
Debug: rlm_ldap: LDAP radiusServiceType mapped to RADIUS Service-Type
Debug: rlm_ldap: LDAP radiusFramedProtocol mapped to RADIUS Framed-Protocol
Debug: rlm_ldap: LDAP radiusFramedRoute mapped to RADIUS Framed-Route
Debug: rlm_ldap: LDAP radiusFramedRouting mapped to RADIUS Framed-Routing
Debug: rlm_ldap: LDAP radiusFilterId mapped to RADIUS Filter-Id
Debug: rlm_ldap: LDAP radiusFramedMTU mapped to RADIUS Framed-MTU
Debug: rlm_ldap: LDAP radiusLoginIPHost mapped to RADIUS Login-IP-Host
Debug: rlm_ldap: LDAP radiusLoginService mapped to RADIUS Login-Service
Debug: rlm_ldap: LDAP radiusLoginTCPPort mapped to RADIUS Login-TCP-Port
Debug: rlm_ldap: LDAP radiusCallbackNumber mapped to RADIUS Callback-Number
Debug: rlm_ldap: LDAP radiusCallbackId mapped to RADIUS Callback-Id
Debug: rlm_ldap: LDAP radiusClass mapped to RADIUS Class
Debug: rlm_ldap: LDAP radiusSessionTimeout mapped to RADIUS Session-Timeout
Debug: rlm_ldap: LDAP radiusIdleTimeout mapped to RADIUS Idle-Timeout
Debug: rlm_ldap: LDAP radiusLoginLATNode mapped to RADIUS Login-LAT-Node
Debug: rlm_ldap: LDAP radiusLoginLATGroup mapped to RADIUS Login-LAT-Group
Debug: rlm_ldap: LDAP radiusPortLimit mapped to RADIUS Port-Limit
Debug: rlm_ldap: LDAP radiusLoginLATPort mapped to RADIUS Login-LAT-Port
Debug: rlm_ldap: LDAP radiusReplyMessage mapped to RADIUS Reply-Message
Debug: rlm_ldap: LDAP radiusTunnelType mapped to RADIUS Tunnel-Type
One last thing, we have to add radiusprofile objectClass and dialupAceess attribute to user rkhan
You can do it right on console, but I would use ldif file
> nano /tmp/modify.ldif
And paste the following in it
> dn: uid=rkhan,ou=Users,dc=myldap,dc=ent
changetype: modify
add: objectClass
objectClass: radiusprofile

dn: uid=rkhan,ou=Users,dc=myldap,dc=ent
changetype: modify
add: dialupAccess
dialupAccess: access_attr
Issue the following command to add above entries in user rkhan records
> sudo ldapmodify -h localhost -p 389 -D "cn=admin,dc=myldap,dc=ent" -w mypassword -f /tmp/modify.ldif
At this point freeradius is all setup with ldap authentication and only rkhan can use freeradius to authenticate against open-ldap.
Setup/allow client, localhost is allowed by default
> nano /etc/freeradius/clients.conf Look through the file and make changes where needed
Configure wireless or wired clients and have fun !
I have tested it with my wireless [eap/peap authentication method] setup and it work like a charm everytime
Enjoy!

You can also access this articles at 
[[COLOR="Blue"]my website[/COLOR]]("http://cns.selfip.net/articles/ldap-frad.php")

I already have wrote php script to add user via a web page, it will take care of all 1zz and 2zz in background.
User/administrator just have to fill the form and hit submit and yea ! our new user is ready to use freeradius and can authenticate against our freshly configured ldap server

Let me know if you are interested in that script

Note:- I have tested this setup using plain text password in ldap database

Feel free to email me if you have any question(s)

---

