---
title: "Setup OpenLDAP on Ubuntu 16.04 LTS"
date: 2016-04-29
forum: Server Platforms
---

### Post by Ryaz_Khan on 2016-04-29
**Disclaimer**
> Be advised that I do not issue any sort of warranty or take the responsibility that below setup will work for you without any issues, it did worked for me with no issues so I am just sharing it for the community. My advance apology for any typo I might have. Feel free to ask any question(s) you may have.[B]
Setup parameters[/B]
> 
[I]name: dc1
domain/tree: devlab.nt
ip: 192.168.1.30 
admin pass: test
rkhan pass: test
[/I]
The basic dn comes from /etc/hosts so make sure you check it before proceeding. Here are mine for reference
> 127.0.0.1       localhost
192.168.1.30    dc1.devlab.nt   dc1


# The following lines are desirable for IPv6 capable hosts
::1     localhost ip6-localhost ip6-loopback
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters


**Installation**
```
sudo apt install slapd ldap-utils libnss-ldap
```
answers
> test
test
ldap://127.0.0.1
dc=devlab,dc=nt
3
Yes
No
cn=admin,dc=devlab,dc=nt
test
**Configuration**
enable logs via ldif, copy and paste below code in terminal
```
cat << eot > log.ldif
dn: cn=config
changetype: modify
add: olcLogLevel
olcLogLevel: stats
eot
```
add above ldif
```
sudo ldapmodify -Q -Y EXTERNAL -H ldapi:/// -f log.ldif
```
enable LDAP profile for NSS
```
sudo auth-client-config -t nss -p lac_ldap
```
update authentication methods, select ldap if not selected already
```
sudo pam-auth-update
```
edit */etc/ldap.conf* and change/uncomment these values
> host 127.0.0.1
base dc=home,dc=nt
uri ldap://127.0.0.1/
rootbinddn cn=admin,dc=devlab,dc=nt
ldap_version 3
bind_policy soft
enable some indexes via ldif, copy and paste below code in terminal
```
cat << eot > indexes.ldif
dn: olcDatabase={1}hdb,cn=config
changetype: modify
add: olcDbIndex
olcDbIndex: uid eq,pres,sub
eot
```
add above ldif, copy and paste below code in terminal
```
sudo ldapmodify -Q -Y EXTERNAL -H ldapi:/// -f indexes.ldif
```
**Directory population**
add basic structure/tree, copy and paste below code in terminal
```
cat << eot > base.ldif
dn: OU=people,DC=devlab,DC=nt
changetype: add
objectClass: top
objectClass: organizationalunit
description: People OU

dn: OU=groups,DC=devlab,DC=nt
changetype: add
objectClass: top
objectClass: organizationalunit
description: Groups OU


dn: OU=machines,DC=devlab,DC=nt
changetype: add
objectClass: top
objectClass: organizationalunit
description: Machines OU
eot
```
add above ldif
```
ldapadd -x -D cn=admin,dc=devlab,dc=nt -w test -f base.ldif
```
add some groups, copy and paste below code in terminal
```
cat << eot > group.ldif
dn: cn=radius,ou=groups,dc=devlab,dc=nt
changetype: add
objectclass: top
objectclass: groupOfNames
cn: Administrators
member: 

dn: cn=vpn,ou=groups,dc=devlab,dc=nt
changetype: add
objectclass: top
objectclass: groupOfNames
cn: vpn
member: 
eot

```
add above ldif
```
ldapadd -x -D cn=admin,dc=devlab,dc=nt -w test -f group.ldif
```
add first user via ldif, copy and paste below code in terminal
```
cat << eot > user.ldif
dn: uid=rkhan,ou=people,dc=devlab,dc=nt
objectClass: organizationalPerson
objectClass: person
objectClass: top
objectClass: inetOrgPerson
objectClass: posixAccount
objectClass: shadowAccount
uid: rkhan
sn: Khan
givenName: Ryaz
cn: Ryaz Khan
displayName: Ryaz Khan
uidNumber: 10000
gidNumber: 10000
userPassword: {SSHA}test
gecos: Ryaz Khan
loginShell: /bin/bash
homeDirectory: /profiles/rkhan
mail: [EMAIL="rkhan@devlab.nt"]rkhan@devlab.nt[/EMAIL]
telephoneNumber: 000-000-0000
st: NY
manager: uid=rkhan,ou=people,dc=devlab,dc=nt
shadowExpire: -1
shadowFlag: 0
shadowWarning: 7
shadowMin: 8
shadowMax: 999999
shadowLastChange: 10877
title: System Administrator
eot
```
add above ldif
```
ldapadd -x -D cn=admin,dc=devlab,dc=nt -w test -f user.ldif
```
**Administration**
reset ldap password for rkhan (optional)
```
ldappasswd -H ldapi:/// -x -D "cn=admin,dc=devlab,dc=nt" -w test -s test "uid=rkhan,ou=people,dc=devlab,dc=nt"
```
add rkhan to radius and vpn group. You could add in user.ldif as well, copy and paste below code in terminal
```
cat << eot > modify.ldif
dn: cn=radius,ou=groups,dc=devlab,dc=nt
changetype: modify
add: member
member: uid=rkhan,ou=people,dc=devlab,dc=nt

dn: cn=vpn,ou=groups,dc=devlab,dc=nt
changetype: modify
add: member
member: uid=rkhan,ou=people,dc=devlab,dc=nt
eot

```
add above ldif to ldap database
```
sudo ldapmodify -h localhost -p 389 -D "cn=admin,dc=devlab,dc=nt" -w test -f modify.ldif
```
restart ldap service
```
sudo systemctl restart slapd.service
```
Congrats ! You have full working ldap server. Test it out and ssh rkhan to local system
```
ssh rkhan@localhost
```
**Starting over**
uninstall packages
```
sudo apt purge slapd ldap-utils libnss-ldap
```
delete ldap database if exists
```
rm /var/lib/ldap/*
```
**Troubleshooting**
reconfigure base dn and admin account
```
sudo dpkg-reconfigure slapd
```
answers
> No
devlab.nt
devlab.nt
test
test
HDB
Yes
Yes
No
verify dn
```
ldapsearch -x -LLL -H ldap:/// -b "dc=devlab,dc=nt" dn
```

As I mentioned above, feel free to contact me at [http://ryaz.homeip.net/?nod=6](http://ryaz.homeip.net/?nod=6) if you have any question(s).

This tutorial also can be found at [http://ryaz.homeip.net/?p=78](http://ryaz.homeip.net/?p=78)

---

