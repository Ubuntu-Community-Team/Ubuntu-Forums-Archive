---
title: "Ubuntu Server 10.04 LTS LDAP (openldap) problem"
date: 2010-06-18
forum: Server Platforms
---

### Post by madneon on 2010-06-18
Hi!

I can't manage to authenticate against **openldap** server, I've been stuck with it for weeks now on **10.04**, and I had problems before on **9.10** - I did upgrade hoping to have it fixed with LTS version... I really have no more ideas how to get it right... Following official documentation found at: [https://help.ubuntu.com/10.04/serverguide/C/openldap-server.html](https://help.ubuntu.com/10.04/serverguide/C/openldap-server.html), and many other tutorials around the web I came up with a "make" script. Can anyone help me find whats wrong with it?

```

#!/bin/bash

fqdn="dc=company,dc=com"
organisation="Company"
admin_pass_plain="aaa"
uri="ldapi://%2fvar%2frun%2fslapd%2fldapi/"

# ----------------------------------------------------------------

mkdir -p tmp
chmod 750 tmp

echo;echo "Installing packages"
aptitude -y install slapd ldap-utils ldapscripts

admin_pass=`slappasswd -s $admin_pass_plain`

echo;echo "Base schemas"

ldapadd -Y EXTERNAL -H ldapi:/// -f /etc/ldap/schema/cosine.ldif
ldapadd -Y EXTERNAL -H ldapi:/// -f /etc/ldap/schema/nis.ldif
ldapadd -Y EXTERNAL -H ldapi:/// -f /etc/ldap/schema/inetorgperson.ldif

echo;echo "Backend"

cat > tmp/backend.ldif << EOF
dn: cn=module,cn=config
objectClass: olcModuleList
cn: module
olcModulepath: /usr/lib/ldap
olcModuleload: back_hdb

dn: olcDatabase=hdb,cn=config
objectClass: olcDatabaseConfig
objectClass: olcHdbConfig
olcDatabase: {1}hdb
olcSuffix: $fqdn
olcDbDirectory: /var/lib/ldap
olcRootDN: cn=admin,$fqdn
olcRootPW: $admin_pass
olcDbConfig: set_cachesize 0 2097152 0
olcDbConfig: set_lk_max_objects 1500
olcDbConfig: set_lk_max_locks 1500
olcDbConfig: set_lk_max_lockers 1500
olcDbIndex: objectClass eq
olcLastMod: TRUE
olcDbCheckpoint: 512 30

olcAccess: to attrs=userPassword by dn="cn=admin,$fqdn" write by anonymous auth by self write by * none
olcAccess: to attrs=shadowLastChange by self write by * read
olcAccess: to dn.base="" by * read
olcAccess: to * by dn="cn=admin,$fqdn" write by * read
EOF

ldapadd -Y EXTERNAL -H ldapi:/// -f tmp/backend.ldif

echo;echo "Frontend"

cat > tmp/frontend.ldif << EOF
dn: $fqdn
objectClass: top
objectClass: dcObject
objectclass: organization
o: $organisation
dc: $organisation
description: $organisation

dn: cn=admin,$fqdn
objectClass: simpleSecurityObject
objectClass: organizationalRole
cn: admin
description: LDAP administrator
userPassword: $admin_pass

dn: ou=people,$fqdn
objectClass: organizationalUnit
ou: people

dn: ou=groups,$fqdn
objectClass: organizationalUnit
ou: groups

dn: ou=machines,$fqdn
objectClass: organizationalUnit
ou: machines
EOF

ldapadd -x -D cn=admin,$fqdn -w $admin_pass_plain -f tmp/frontend.ldif

echo;echo "Indexes"

cat > tmp/indexes.ldif << EOF
dn: olcDatabase={1}hdb,cn=config
add: olcDbIndex
olcDbIndex: uid eq,pres,sub
olcDbIndex: uidNumber eq
olcDbIndex: gidNumber eq
olcDbIndex: memberUid eq
olcDbIndex: uniqueMember eq
EOF

ldapmodify -Y EXTERNAL -H ldapi:/// -f tmp/indexes.ldif

echo;echo "TLS"

aptitude -y install gnutls-bin
sh -c "certtool --generate-privkey > /etc/ssl/private/cakey.pem"
cat > /etc/ssl/ca.info << EOF
cn = $organisation
ca
cert_signing_key
EOF

certtool --generate-self-signed --load-privkey /etc/ssl/private/cakey.pem --template /etc/ssl/ca.info --outfile /etc/ssl/certs/cacert.pem

sh -c "certtool --generate-privkey > /etc/ssl/private/$hostname""_slapd_key.pem"

cat > /etc/ssl/$hostname.info << EOF
organization = $organisation
cn = $hostname.$domainname
tls_www_server
encryption_key
signing_key
EOF

certtool --generate-certificate --load-privkey /etc/ssl/private/$hostname""_slapd_key.pem \
 --load-ca-certificate /etc/ssl/certs/cacert.pem --load-ca-privkey /etc/ssl/private/cakey.pem \
 --template /etc/ssl/$hostname.info --outfile /etc/ssl/certs/$hostname""_slapd_cert.pem

cat > tmp/tls.ldif << EOF
dn: cn=config
add: olcTLSCACertificateFile
olcTLSCACertificateFile: /etc/ssl/certs/cacert.pem
-
add: olcTLSCertificateFile
olcTLSCertificateFile: /etc/ssl/certs/$hostname"_slapd_cert.pem
-
add: olcTLSCertificateKeyFile
olcTLSCertificateKeyFile: /etc/ssl/private/$hostname"_slapd_key.pem
EOF

sed -i 's/"_slapd/_slapd/g' tmp/tls.ldif
ldapmodify -Y EXTERNAL -H ldapi:/// -f tmp/tls.ldif

sed -i 's/SLAPD_SERVICES="ldap:\/\/\/ ldapi:\/\/\/"/SLAPD_SERVICES="ldap:\/\/\/ ldapi:\/\/\/ ldaps:\/\/\/"/g' /etc/default/slapd

adduser openldap ssl-cert
chgrp ssl-cert /etc/ssl/private/$hostname""_slapd_key.pem
chmod g+r /etc/ssl/private/$hostname""_slapd_key.pem

/etc/init.d/slapd restart

echo;echo "Authentication"

cat > /etc/ldap.conf << EOF
base $fqdn
uri $uri
ldap_version 3
#binddn
#bindpw
rootbinddn cn=admin,$fqdn
timelimit 5
bind_timelimit 5
pam_password md5
EOF

ln -fs ../ldap.conf /etc/ldap/ldap.conf

cat > /etc/ldapscripts/ldapscripts.conf << EOF
SERVER="$uri"
BINDDN="cn=admin,$fqdn"
#BINDPWDFILE="/etc/ldapscripts/ldapscripts.passwd"
BINDPWDFILE="/etc/ldap.secret"

SUFFIX="$fqdn"
GSUFFIX="ou=groups"
USUFFIX="ou=people"
MSUFFIX="ou=machines"

GIDSTART="10000"
UIDSTART="10000"
MIDSTART="20000"

CREATEHOMES="no"

PASSWORDGEN="<ask>"

RECORDPASSWORDS="no"
PASSWORDFILE="/var/log/ldapscripts_passwd.log"

LOGFILE="/var/log/ldapscripts.log"

TMPDIR="/tmp"

LDAPSEARCHBIN="/usr/bin/ldapsearch"
LDAPADDBIN="/usr/bin/ldapadd"
LDAPDELETEBIN="/usr/bin/ldapdelete"
LDAPMODIFYBIN="/usr/bin/ldapmodify"
LDAPMODRDNBIN="/usr/bin/ldapmodrdn"
LDAPPASSWDBIN="/usr/bin/ldappasswd"

GETENTPWCMD="getent passwd"
GETENTGRCMD="getent group"

GTEMPLATE=""
UTEMPLATE=""
MTEMPLATE=""
EOF

rm /etc/ldapscripts/ldapscripts.passwd

aptitude -y install libnss-ldap

echo -n $admin_pass_plain > /etc/ldap.secret
chmod 400 /etc/ldap.secret

auth-client-config -t nss -p lac_ldap

pam-auth-update

echo "session required pam_mkhomedir.so" > /etc/pam.d/common-session.new
cat /etc/pam.d/common-session >> /etc/pam.d/common-session.new
mv /etc/pam.d/common-session.new /etc/pam.d/common-session

#rm -rf tmp

```

After this configuration I'm able to use **ldapscripts** to add, remove groups, people etc. but I'm unable to login. I can **getent group** and **getent passwd** from root, but not from unprivileged user.

Also after "su" into LDAP user from root i get "I have no name!" and "groups: cannot find name for group ID ...". Where else should I look except "/etc/pam.d", and "/etc/nsswitch.conf"?

I need to be able to login LDAP users on local server and also login from remote machines, so any hints about configuring client machines will be appreciated.

---

### Post by denarced on 2010-06-20
How are you trying to login?

---

### Post by DaveVentresca on 2010-06-20
On your client machines you'll need to install libnss-ldapd (if you're clients are on 10.04, libnss-ldap if they're on earlier versions), libpam-ldapd (same deal, libpam-ldap for earlier versions) and ldap-auth-client. 

Then you'll need to edit the /etc/ldap/ldap.conf, /etc/nsswitch, & /etc/pam.d/common-session to suit your needs.

make sure that /etc/ldap/ldap.conf has: (where your.domain.local = whatever your ldap domain is)

BASE  dc=your,dc=domain,dc=local
URI    ldap.your.domain.local
TLS_REQCERT    demand
TLS_CACERT      /etc/ssl/certs/cacert_home.pem

make sure that /etc/nsswitch.conf says 'files' instead of 'compat'

and the common-session file you're on your own... I noticed that you don't have your ldap set up to create home directories for the ldap users. is that intentional? I am by no means an expert, but I have gotten my ldap users to authenticate off the server and login graphically on client machines in the local network. one thing that you can use to test your ldap accounts is ssh. e.g. at a terminal window on a client machine, type in ssh (ldap-user-name)@(your-server-ip) & hit enter, it will ask you to confirm that you're adding that IP to the ssh profile on the client, but then it will ask you for a password & if you can login using ssh, then you should be able to graphically login...

---

### Post by madneon on 2010-06-20
> **denarced said:**
> How are you trying to login?

The only way I'm able to login as LDAP user is by **su** from root, but I got "I have no name!" instead of real login name. I'm unable to su from normal user or login from console/ssh - it doesn't accept correct password.

---

### Post by madneon on 2010-06-20
> **DaveVentresca said:**
> On your client machines you'll need to install libnss-ldapd (if you're clients are on 10.04, libnss-ldap if they're on earlier versions), libpam-ldapd (same deal, libpam-ldap for earlier versions) and ldap-auth-client. 

I just noticed that there are two name caching deamons running: **nscd** and **nslcd** - aren't they conflicting somehow? What deamon is running on your LDAP server?

> I noticed that you don't have your ldap set up to create home directories for the ldap users. is that intentional?
Yes, I added *"session required pam_mkhomedir.so"* to  **/etc/pam.d/common-session** - the home directory is created for user on his first login.

How did you manage to start LDAP server on 10.04? Can you plase give step-by-step guide or point me to any correct web-tutorial?

---

### Post by DaveVentresca on 2010-06-20
try this tutorial [http://www.opinsys.fi/setting-up-openldap-on-ubuntu-10-04-alpha2](http://www.opinsys.fi/setting-up-openldap-on-ubuntu-10-04-alpha2). it's the one that finally worked for me.

---

### Post by madneon on 2010-06-20
> **DaveVentresca said:**
> try this tutorial [http://www.opinsys.fi/setting-up-openldap-on-ubuntu-10-04-alpha2](http://www.opinsys.fi/setting-up-openldap-on-ubuntu-10-04-alpha2). it's the one that finally worked for me.

Tried that... It doesn't work for me on 10.04 LTS final release...

First after this tutorial **ldapscripts** don't work, to fix this read: [http://ubuntuforums.org/showthread.php?t=1488232](http://ubuntuforums.org/showthread.php?t=1488232) and replace */usr/share/ldapscripts/runtime.debian*.

Than, one have to add to */etc/ldapscripts/ldapscripts.conf*:
```

GIDSTART="10000"
UIDSTART="10000"
MIDSTART="20000"

```

After all this, I'm unable to login LDAP users anyway...

---

### Post by DaveVentresca on 2010-06-20
not sure... the opinsys tutorial worked fine for me on a 9.10 server. not sure what else to tell you.

---

### Post by madneon on 2010-09-01
Does anyone have a solution on starting OpenLDAP on Ubuntu Server 10.04?

---

