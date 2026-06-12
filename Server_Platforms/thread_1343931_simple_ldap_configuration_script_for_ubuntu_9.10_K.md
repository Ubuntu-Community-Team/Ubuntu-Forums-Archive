---
title: "simple ldap configuration script for ubuntu 9.10 Karmic Koala"
date: 2009-12-02
forum: Server Platforms
---

### Post by evilscare on 2009-12-02
Just writed a simple configuration script for ldap configuration script for ubuntu 9.10 Karmic Koala, hope it helps ;)

this script is based on the howto posted by apalacheno at this link [http://ubuntuforums.org/showthread.php?t=1313472](http://ubuntuforums.org/showthread.php?t=1313472)

WARNING:
This script is very simple (i've writed for my needs) and it can handle only level 1 domains (home.com for example), the only thing I've  checked is the admin password insertion... so pay attention at what you write when asked for your domain name :)

run this from root user

Sorry for my very bad english... i'm italian... and my English teacher too

> 
#!/bin/bash

apt-get install slapd ldap-utils

ldapadd -Y EXTERNAL -H ldapi:/// -f /etc/ldap/schema/cosine.ldif;\
ldapadd -Y EXTERNAL -H ldapi:/// -f /etc/ldap/schema/inetorgperson.ldif;\
ldapadd -Y EXTERNAL -H ldapi:/// -f /etc/ldap/schema/nis.ldif

echo 'insert your domain name (ex: dc=home,dc=com): '

read -e domain

passChecked=0
while [ $passChecked -eq 0 ]
do
echo "insert password for user admin:"
read -es pass
echo "repeat password for user admin:"
read -es passControl

echo $pass
echo $passControl
if [ $pass = $passControl ];then 
    passChecked=1
else
    echo "passwords don't match"
fi
done

echo "###########################################################
# DATABASE SETUP
###########################################################

# Load modules for database type
dn: cn=module{0},cn=config
objectClass: olcModuleList
cn: module{0}
olcModulePath: /usr/lib/ldap
olcModuleLoad: {0}back_hdb

# Create directory database
dn: olcDatabase={1}hdb,cn=config
objectClass: olcDatabaseConfig
objectClass: olcHdbConfig
olcDatabase: {1}hdb
olcDbDirectory: /var/lib/ldap
olcSuffix: $domain
olcRootDN: cn=admin,$domain
olcRootPW: $pass
olcAccess: {0}to attrs=userPassword,shadowLastChange by dn=\"cn=admin,$domain\" write by anonymous auth by self write by * none
olcAccess: {1}to dn.base="" by * read
olcAccess: {2}to * by dn=\"cn=admin,$domain\" write by * read
olcLastMod: TRUE
olcDbCheckpoint: 512 30
olcDbConfig: {0}set_cachesize 0 2097152 0
olcDbConfig: {1}set_lk_max_objects 1500
olcDbConfig: {2}set_lk_max_locks 1500
olcDbConfig: {3}set_lk_max_lockers 1500
olcDbIndex: uid pres,eq
olcDbIndex: cn,sn,mail pres,eq,approx,sub
olcDbIndex: objectClass eq


###########################################################
# DEFAULTS MODIFICATION
###########################################################
# Some of the defaults need to be modified in order to allow
# remote access to the LDAP config. Otherwise only root
# will have administrative access.

dn: cn=config
changetype: modify
delete: olcAuthzRegexp

dn: olcDatabase={-1}frontend,cn=config
changetype: modify
delete: olcAccess

dn: olcDatabase={0}config,cn=config
changetype: modify
add: olcRootPW
olcRootPW: `slappasswd -s $pass`

dn: olcDatabase={0}config,cn=config
changetype: modify
delete: olcAccess" > conf.ldif

echo 
ldapadd -Y EXTERNAL -H ldapi:/// -f conf.ldif

domainmod=(`echo $domain | sed -e "s/\,//g"`)
domainmod=(`echo $domainmod | sed -e "s/\dc//g"`)
domainarray=(`echo $domainmod | tr '=' ' '`)

echo "# Tree root
dn: $domain
objectClass: dcObject
objectclass: organization
o: ${domainarray[0]}.${domainarray[1]}
dc: ${domainarray[0]}
description: Tree root

# LDAP admin
dn: cn=admin,$domain
objectClass: simpleSecurityObject
objectClass: organizationalRole
cn: admin
userPassword: $pass
description: LDAP administrator" > base.ldif

ldapadd -x -D cn=admin,$domain -W -f base.ldif
enjoy

---

### Post by lurchnz on 2009-12-02
adding new entry "olcDatabase={1}hdb,cn=config"
ldap_add: Invalid syntax (21)
        additional info: olcSuffix: value #0 invalid per syntax

Enter LDAP Password:
ldap_bind: Invalid DN syntax (34)

---

### Post by evilscare on 2009-12-03
Please paste the conf.ldif file created by the script for debugging

---

### Post by lurchnz on 2009-12-03
Hmm, well I've looked through the ldap folder and can not find the file conf.ldif anywhere. 

/etc/ldap

---

### Post by evilscare on 2009-12-04
[SIZE=+1]the script dump the conf.ldif file in the same folder where it's launched
[/SIZE]

---

