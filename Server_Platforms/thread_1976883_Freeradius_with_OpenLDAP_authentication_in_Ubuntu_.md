---
title: "Freeradius with OpenLDAP authentication in Ubuntu 12.04 LTS"
date: 2012-05-09
forum: Server Platforms
---

### Post by ryazkhan on 2012-05-09
Hi folks,

Its me again with one new tutorial, I like Ubuntu Sever LTS editions so for the most part all of my tutorials are based on LTS editions. Lets get back 

With the assumption that Ubuntu 12.04 LTS Server is already installed. No assurance that it will work for your setup, worked for me so I am sharing it

I am assuming that ldap is already installed and configured correctly, [[COLOR="Blue"]see this guide[/COLOR]]("http://www.ryazkhan.net/articles/ldap12") if you need to install and configure ldap up
My domain/tree is dc=testlab,dc=dev and administrator account is cn=admin,dc=testlab,dc=dev and administrator password is test feel free to change it to your liking

Update all packages and install updates if any
> apt-get update && apt-get upgrade -y
Install freeradius and relevant required packages
> apt-get install freeradius freeradius-ldap -y
Copy freeradius schema for ldap
> cp /usr/share/doc/freeradius/examples/openldap.schema /etc/ldap/schema/
Add openldab schema to ldap database, but before adding it lets check it to make sure that its already does exist
> 
sudo ldapsearch -Q -LLL -Y EXTERNAL -H ldapi:/// -b \ cn=schema,cn=config dn

in my setup it was not there so I am adding it, it might be in your setup
Create a schema placeholder (file)
> nano schema.conf
and paste the following in it
> include /etc/ldap/schema/openldap.schema
Create ldif data holder directory 
> mkdir out
Convert the schema to ldif format

> slapcat -f schema.conf -F out -n0 -H ldap:///cn={0}openldap,cn=schema,cn=config -l cn=openldap.ldif
Now you will have openldap schema in ldif format, schema need to be cleaned little otherwise you will get some nasty errors at some point, so lets do that > nano cn\=openldap.ldif
and change
> 
dn: cn={0}openldap,cn=schema,cn=config
objectClass: olcSchemaConfig
cn: {0}openldap

with
> 
dn: cn=openldap,cn=schema,cn=config
objectClass: olcSchemaConfig
cn: openldap

above lines are located in the beginning of the ldif file, while in that file remove these line, they are located on the bottom of ldif file, then save the file and exit out of it
> 
structuralObjectClass: olcSchemaConfig
entryUUID: 85d35afa-2992-1031-8f93-0d1d8c5b6386
creatorsName: cn=config
createTimestamp: 20120503173822Z
entryCSN: 20120503173822.097163Z#000000#000#000000
modifiersName: cn=config
modifyTimestamp: 20120503173822Z

Now the schema is ready to be added to ldap database, lets do that
> 
sudo ldapadd -Q -Y EXTERNAL -H ldapi:/// -f cn\=openldap.ldif

there would not be any errors, if there are then check your configuration over
Lets verify the new schema
> 
sudo ldapsearch -Q -LLL -Y EXTERNAL -H ldapi:/// -b cn=schema,cn=config dn

it should be there, mine was !
Before moving any further I will just restart both ldap and freeradius server just to be sure
> 
service slapd restart
service freeradius restart

Lets make the ldap connection, please backup your configuration before making any changes so you will have the option to roll back if something goes wrong
> 
nano /etc/freeradius/modules/ldap

and make sure of following at least, adjust the configs according to your setup, save the file and exit out of it
> 
server = "localhost"
identity = "cn=admin,dc=testlab,dc=dev"
password = test
basedn = "ou=Users,dc=testlab,dc=dev"
filter = "(uid=%{%{Stripped-User-Name}:-%{User-Name}})"
base_filter = "(objectclass=radiusprofile)"
access_attr = "dialupAccess"
password_attribute = userPassword 

Tell freeradius to use ldap for authentication by edit the following file
> 
nano /etc/freeradius/sites-enabled/default

Uncomment the following, ldap is located under authorize and rest is located under authenticate
> 
ldap
Auth-Type LDAP {
                ldap
        }

Also tell freeradius to use ldap within tunnel as well, otherwise it simply would not work
> 
nano /etc/freeradius/sites-enabled/inner-tunnel

and uncomment all ldap entries or at least line 142 (ldap), located under authorized area
We are pretty much done, so restart both monster [ldap and freeradius] just to be safe 
> 
service slapd restart
service freeradius restart 

Lets check the ldap mapping, start freeradius in debug mode
> 
freeradius -XXX

if you see the following then our mapping is work, rock on ! 
> 
Debug: rlm_ldap: reading ldap<->radius mappings from file /etc/freeradius/ldap.attrmap
Debug: rlm_ldap: LDAP radiusCheckItem mapped to RADIUS $GENERIC$
Debug: rlm_ldap: LDAP radiusReplyItem mapped to RADIUS $GENERIC$
Debug: rlm_ldap: LDAP radiusAuthType mapped to RADIUS Auth-Type
Debug: rlm_ldap: LDAP radiusSimultaneousUse mapped to RADIUS Simultaneous-Use
Debug: rlm_ldap: LDAP radiusCalledStationId mapped to RADIUS Called-Station-Id
Debug: rlm_ldap: LDAP radiusCallingStationId mapped to RADIUS Calling-Station-Id
Debug: rlm_ldap: LDAP lmPassword mapped to RADIUS LM-Password
Debug: rlm_ldap: LDAP ntPassword mapped to RADIUS NT-Password
Debug: rlm_ldap: LDAP sambaLmPassword mapped to RADIUS LM-Password
Debug: rlm_ldap: LDAP sambaNtPassword mapped to RADIUS NT-Password
Debug: rlm_ldap: LDAP dBCSPwd mapped to RADIUS LM-Password
Debug: rlm_ldap: LDAP userPassword mapped to RADIUS Password-With-Header
Debug: rlm_ldap: LDAP acctFlags mapped to RADIUS SMB-Account-CTRL-TEXT
Debug: rlm_ldap: LDAP radiusExpiration mapped to RADIUS Expiration
Debug: rlm_ldap: LDAP radiusNASIpAddress mapped to RADIUS NAS-IP-Address
Debug: rlm_ldap: LDAP radiusServiceType mapped to RADIUS Service-Type
Debug: rlm_ldap: LDAP radiusFramedProtocol mapped to RADIUS Framed-Protocol
Debug: rlm_ldap: LDAP radiusFramedIPAddress mapped to RADIUS Framed-IP-Address
Debug: rlm_ldap: LDAP radiusFramedIPNetmask mapped to RADIUS Framed-IP-Netmask
Debug: rlm_ldap: LDAP radiusFramedRoute mapped to RADIUS Framed-Route
Debug: rlm_ldap: LDAP radiusFramedRouting mapped to RADIUS Framed-Routing
Debug: rlm_ldap: LDAP radiusFilterId mapped to RADIUS Filter-Id
Debug: rlm_ldap: LDAP radiusFramedMTU mapped to RADIUS Framed-MTU
Debug: rlm_ldap: LDAP radiusFramedCompression mapped to RADIUS Framed-Compression
Debug: rlm_ldap: LDAP radiusLoginIPHost mapped to RADIUS Login-IP-Host
Debug: rlm_ldap: LDAP radiusLoginService mapped to RADIUS Login-Service
Debug: rlm_ldap: LDAP radiusLoginTCPPort mapped to RADIUS Login-TCP-Port
Debug: rlm_ldap: LDAP radiusCallbackNumber mapped to RADIUS Callback-Number
Debug: rlm_ldap: LDAP radiusCallbackId mapped to RADIUS Callback-Id
Debug: rlm_ldap: LDAP radiusFramedIPXNetwork mapped to RADIUS Framed-IPX-Network
Debug: rlm_ldap: LDAP radiusClass mapped to RADIUS Class
Debug: rlm_ldap: LDAP radiusSessionTimeout mapped to RADIUS Session-Timeout
Debug: rlm_ldap: LDAP radiusIdleTimeout mapped to RADIUS Idle-Timeout
Debug: rlm_ldap: LDAP radiusTerminationAction mapped to RADIUS Termination-Action
Debug: rlm_ldap: LDAP radiusLoginLATService mapped to RADIUS Login-LAT-Service
Debug: rlm_ldap: LDAP radiusLoginLATNode mapped to RADIUS Login-LAT-Node
Debug: rlm_ldap: LDAP radiusLoginLATGroup mapped to RADIUS Login-LAT-Group
Debug: rlm_ldap: LDAP radiusFramedAppleTalkLink mapped to RADIUS Framed-AppleTalk-Link
Debug: rlm_ldap: LDAP radiusFramedAppleTalkNetwork mapped to RADIUS Framed-AppleTalk-Network
Debug: rlm_ldap: LDAP radiusFramedAppleTalkZone mapped to RADIUS Framed-AppleTalk-Zone
Debug: rlm_ldap: LDAP radiusPortLimit mapped to RADIUS Port-Limit
Debug: rlm_ldap: LDAP radiusLoginLATPort mapped to RADIUS Login-LAT-Port
Debug: rlm_ldap: LDAP radiusReplyMessage mapped to RADIUS Reply-Message
Debug: rlm_ldap: LDAP radiusTunnelType mapped to RADIUS Tunnel-Type
Debug: rlm_ldap: LDAP radiusTunnelMediumType mapped to RADIUS Tunnel-Medium-Type
Debug: rlm_ldap: LDAP radiusTunnelPrivateGroupId mapped to RADIUS Tunnel-Private-Group-Id

So far so good ? Lets add a test user to your ldap if you already have not one 
> nano base.ldif
and paste the following
> 
dn: ou=Users,dc=testlab,dc=dev
objectClass: organizationalUnit
ou: Users

dn: uid=rkhan,ou=Users,dc=testlab,dc=dev
objectClass: organizationalPerson
objectClass: person
objectClass: top
objectClass: inetOrgPerson
objectClass: posixAccount
objectClass: shadowAccount
objectClass: radiusprofile
dialupAccess: access_attr
uid: rkhan
sn: Khan
givenName: Ryaz
cn: Ryaz Khan
displayName: Ryaz Khan
uidNumber: 10000
gidNumber: 10000
userPassword: test
gecos: Ryaz Khan
loginShell: /bin/bash
homeDirectory: /profiles/rkhan
mail: [email]me@here.com[/email]
telephoneNumber: 000-000-0000
st: NY
manager: uid=rkhan,ou=Users,dc=testlab,dc=dev
shadowExpire: -1
shadowFlag: 0
shadowWarning: 7
shadowMin: 8
shadowMax: 999999
shadowLastChange: 10877
title: System Administrator

Add the above ldif data
> 
ldapadd -x -D cn=admin,dc=testlab,dc=dev -w test -f base.ldif

If you already have user then add the access attribute to the user profile to allow radius authentication, I have user rkhan already created in my ldap so will try with that
> nano modify.ldif
and paste the following in the file, save it again exit out of it
> 
dn: uid=rkhan,ou=Users,dc=testlab,dc=dev
changetype: modify
add: objectClass
objectClass: radiusprofile

dn: uid=rkhan,ou=Users,dc=testlab,dc=dev
changetype: modify
add: dialupAccess
dialupAccess: access_attr

Lets add/modify the ldif data to ldap database
> 
sudo ldapmodify -h localhost -p 389 -D "cn=admin,dc=testlab,dc=dev" -w test -f modify.ldif

At this point freeradius is all configured with ldap authentication and only rkhan can use authenticate via freeradius using ldap credentials, why only him ? Because only he has dialupAccess attribue
Setup/allow client, localhost is allowed by default
> nano /etc/freeradius/clients.conf
Look through the file and make changes where needed
Lets test it from localhost
> radtest rkhan test localhost 18120 testing123
and you will get the result, mine were as follow
> 
Sending Access-Request of id 155 to 127.0.0.1 port 1812
        User-Name = "rkhan"
        User-Password = "test"
        NAS-IP-Address = 10.10.10.230
        NAS-Port = 18120
rad_recv: Access-Accept packet from host 127.0.0.1 port 1812, id=155, length=20

Configure wireless or wired clients and have fun ! 
I have tested it with my wireless [eap/peap authentication method] setup and it worked like a charm everytime 
Enjoy!

[B][I][U]Note:- I have tested this setup using plain text password in ldap database.
[/U][/I][/B]
Feel free ask any question(s)

This tutorial is also [[COLOR="Blue"]available here[/COLOR]]("http://www.ryazkhan.net/articles/frad12")

---

