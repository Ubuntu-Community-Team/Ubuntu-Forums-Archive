---
title: "Problem with openLDAP install Ubuntu 10.04 Server and client"
date: 2010-11-15
forum: Server Platforms
---

### Post by MyTer on 2010-11-15
There are several parts of problems in my question.
1. Install openLDAP and authenticate clients
2. Simple way to authenticate Ubuntu clients (just like Windows simple domain model, but Linux)

[FONT="Arial"][SIZE="4"]Part 1[/SIZE][/FONT]
What I have done:
I have been working on openLDAP for the past 4 weeks. There is a lot of information on LDAP and I have read a lot of it
There are several guides out there for openLDAP installation on Ubuntu, and I have tried many of them, and reinstalled the server between tests.

I followed the guide:
[https://help.ubuntu.com/10.04/serverguide/C/openldap-server.html](https://help.ubuntu.com/10.04/serverguide/C/openldap-server.html)
with 
cn=admin,dc=example,dc=com

The only part I did on a client was “LDAP Authentication”, the rest I did on the server.

First time I skipped the parts
LDAP replication
Setting up ACL
TLS and SSL 

Every test I did worked except I couldn't authenticate with the client (log into a client and let the server authenticate)

When I I try skipping LDAP replication and go to:
[FONT="Arial"][SIZE="3"]Setting up ACL[/SIZE][/FONT]
**ldapsearch -xLLL -b cn=config -D cn=admin,cn=config -W olcDatabase=hdb olcAccess**

my password doesn’t work, I get 
ldap_bind: Invalid credentials (49)
Although I use the right password.  

Is it OK to skip **Replication**, **ACL**, **TLS and SSL**?

What I need:
To be pointed in a direction to solve the problems I have, any help in that matter will do.

[FONT="Arial"][SIZE="4"]Part 2[/SIZE][/FONT]
Simple way to authenticate Ubuntu clients (just like Windows simple domain model, but Linux)

I have tried to find something similar to Windows client login, but haven't found anything that works.
I just need to be pointed to somewhere to read about the authentication model in Linux. I can work out my from there.

It must be something very simple I am missing, because when I read som echapters in The Ubunutu Bible, I can't find anything on it.

Please advise
](*,)

---

### Post by druhboruch on 2010-11-15
For client authentication I was quite successful with sssd.

[http://ubuntuforums.org/showthread.php?t=1585654&highlight=sss](http://ubuntuforums.org/showthread.php?t=1585654&highlight=sss)

I still have the script I used to setup LDAP server.
I could post it if you need it.

EDIT:
I am running 10.10.  It should work on 10.04 with the new/back ported sssd package.

---

### Post by MyTer on 2010-11-16
Thanks druhboruch

I looked at your link
[http://ubuntuforums.org/showthread.php?t=1585654&highlight=sss](http://ubuntuforums.org/showthread.php?t=1585654&highlight=sss)
I'm trying it now, reinstalling the server, Ubuntu 10.04.1 LTS, and the client, Ubuntu 10.10.

Yes please, could You post Your scripts You used to set up Your LDAP server.

I use LTS, because I thought it was better to use a stable product.
Do You think that it is better to use 10.10?

regards
MyTer

---

### Post by druhboruch on 2010-11-16
I found the long script on the Internet and it is not my original work.
I modified it and adapted it to my needs, so please go through it make all necessary changes.

First install necessary sofware:

```
# apt-get install gnutls-bin
# apt-get install slapd ldap-utils
```

Next, edit /etc/default/slapd 
```
SLAPD_SERVICES="ldap:/// ldapi:/// ldaps:///"

```

Then run the first script to create and install the certificates:

```

#!/bin/sh


tmpdir=/tmp

cat <<EOF > $tmpdir/ca.info
cn = My Organization
ca
cert_signing_key
expiration_days = 3650
EOF


certtool --generate-privkey --outfile cacert.key

certtool --generate-self-signed --load-privkey cacert.key --template /tmp/ca.info --outfile cacert.pem

cat <<EOF > $tmpdir/srv.info
organization = My Organization
cn = ldap.example.com
tls_www_server
encryption_key
signing_key
expiration_days = 3650
EOF


certtool --generate-privkey --outfile slapd-vault.key

certtool --generate-certificate --load-privkey slapd-vault.key --template  /tmp/srv.info --outfile slapd-vault.pem --load-ca-certificate cacert.pem --load-ca-privkey cacert.key

install -D -o openldap -g ssl-cert -m 640 cacert.key /etc/ssl/private/cacert.key
install -D -o root -g root -m 644 cacert.pem /etc/ssl/certs/cacert.pem
install -D -o openldap -g ssl-cert -m 640 slapd-vault.key /etc/ssl/private/slapd-vault.key
install -D -o root -g root -m 644 slapd-vault.pem /etc/ssl/certs/slapd-vault.pem


```

Make sure that ldap can read the certificates:
```

adduser openldap ssl-cert

```

---

### Post by druhboruch on 2010-11-16
Then tell your ldap server about the certificates:

```
#!/bin/sh
ldapmodify -Y EXTERNAL -H ldapi:/// << EOF

dn: cn=config
add: olcTLSCACertificateFile
olcTLSCACertificateFile: /etc/ssl/certs/cacert.pem
-
add: olcTLSCertificateFile
olcTLSCertificateFile: /etc/ssl/certs/slapd-vault.pem
-
add: olcTLSCertificateKeyFile
olcTLSCertificateKeyFile: /etc/ssl/private/slapd-vault.key

EOF

```

---

### Post by druhboruch on 2010-11-16
Now create and popluate ldap database:
Please, check the olcDbIndex lines as they may not be what you need.
After you run this script your ldap server is ready and you just have to populate your database with users and groups.
Happy ldaping.


```

#!/bin/sh
passwd=precious	
dc1=example
dc2=com
hash_pw=`slappasswd -s $passwd`
tmpdir=/tmp
#--------------------------------------------------------------#
ldapadd -Y EXTERNAL -H ldapi:/// -f /etc/ldap/schema/cosine.ldif
ldapadd -Y EXTERNAL -H ldapi:/// -f /etc/ldap/schema/inetorgperson.ldif
ldapadd -Y EXTERNAL -H ldapi:/// -f /etc/ldap/schema/nis.ldif
# ldapadd -Y EXTERNAL -H ldapi:/// -f /etc/ldap/schema/qmail.ldif
# ldapadd -Y EXTERNAL -H ldapi:/// -f /etc/ldap/schema/autofs.ldif
#&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;-#
# database.ldif
#&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;-#
cat <<EOF > $tmpdir/database.ldif
# Load dynamic backend modules
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
olcSuffix: dc=$dc1,dc=$dc2
olcRootDN: cn=admin,dc=$dc1,dc=$dc2
olcRootPW: $hash_pw
olcAccess: {0}to attrs=userPassword,shadowLastChange by dn="cn=admin,dc=$dc1,dc=$dc2" write by anonymous auth by self write by * none
olcAccess: {1}to dn.base="" by * read
olcAccess: {2}to * by dn="cn=admin,dc=$dc1,dc=$dc2" write by * read
olcLastMod: TRUE
olcDbCheckpoint: 512 30
olcDbConfig: {0}set_cachesize 0 2097152 0
olcDbConfig: {1}set_lk_max_objects 1500
olcDbConfig: {2}set_lk_max_locks 1500
olcDbConfig: {3}set_lk_max_lockers 1500
olcDbIndex: uid,uidNumber pres,eq
olcDbIndex: cn,sn,mail pres,eq,approx,sub
olcDbIndex: objectClass eq
################################
#        Modifications
################################

dn: cn=config
changetype: modify

dn: olcDatabase={-1}frontend,cn=config
changetype: modify
delete: olcAccess

dn: olcDatabase={0}config,cn=config
changetype: modify
add: olcRootDN
olcRootDN: cn=admin,cn=config

dn: olcDatabase={0}config,cn=config
changetype: modify
add: olcRootPW
olcRootPW: $hash_pw
EOF
sudo ldapadd -Y EXTERNAL -H ldapi:/// -f $tmpdir/database.ldif
####################################
#         Mini DIT
####################################
cat <<EOF> $tmpdir/dit.ldif
# Tree root

dn: dc=$dc1,dc=$dc2
objectClass: dcObject
objectclass: organization
o: $dc1.$dc2
dc: $dc1
description: Tree root

# Populating
dn: cn=admin,dc=$dc1,dc=$dc2
objectClass: simpleSecurityObject
objectClass: organizationalRole
cn: admin
userPassword: $hash_pw
description: LDAP administrator

dn: ou=people,dc=$dc1,dc=$dc2
ou: people
objectClass: organizationalUnit
objectClass: top

dn: ou=groups,dc=$dc1,dc=$dc2
ou: groups
objectClass: organizationalUnit
objectClass: top

EOF

sudo ldapadd -x -D cn=admin,dc=$dc1,dc=$dc2 -W -f $tmpdir/dit.ldif
```

---

### Post by drednought on 2010-11-17
I am new to the forum, so please, excuse the inelegance of newbee.  I am in the process of exploring using LDAP myself, and would also appreciate a copy of the script from druhburoch.  I'll let you know how I get on.

drednought

---

### Post by MyTer on 2010-11-17
> **druhboruch said:**
> 

First install necessary sofware:

```
# apt-get install gnutls-bin
# apt-get install slapd ldap-utils
```



Thanks druhboruch!
it worked great after a few   :redface:
```

sudo apt-get remove --purge slapd

```

I added 
```

$ sudo apt-get install ssl-cert

```
Otherwise I got a error when running
 (the first script to create and install the certificates),
the last lines in the script.

Now I'm moving on to fixing the client with the link
[http://ubuntuforums.org/showthread.php?t=1585654&highlight=sss](http://ubuntuforums.org/showthread.php?t=1585654&highlight=sss)

Will get back when I get it running.

**drednought**
When You see 
#!/bin/sh   (It's called shebang, I believe) 
in the beginning of the code that druhboruch has contributed, it means that You can take all of the text, save it in a file, and run it.
Some of the commands You need to be a superuser to do.

---

### Post by MyTer on 2010-11-18
I followed
[http://ubuntuforums.org/showthread.php?t=1585654](http://ubuntuforums.org/showthread.php?t=1585654)
but when doing 
```

ldapsearch -x -h ldap.example.com -ZZ -b dc=example,dc=com

```
I got
*ldap_start_tls: connect error (-11)*
When I added line to /etc/hosts on the client
192.168.0.1     ldap.example.com

I get
*ldap_start_tls: Can't contact LDAP server (-1)*

Tried adding host 192.168.0.1 to /etc/ldap/ldap.conf, but it didn't make any difference.

I have googled this, but haven't gotten any closer yet.

Is it possible to get working without TLS first, or is it simple to get TLS working?

I now have to write the password to the client twice, whenever an authentication is required. I have googled it, seems to be connected to an ldap that isn't working. I figured it will solve itself when I get ldap working.

Found a partial solution in the bottom of:
[http://ubuntuforums.org/archive/index.php/t-98205.html](http://ubuntuforums.org/archive/index.php/t-98205.html)

[I][B]to solve this problem, edit /etc/pam.d/common-auth file and add "try_first_pass :)
======================================================
auth sufficient pam_ldap.so
auth required pam_unix.so nullok_secure try_first_pass
======================================================[/B][/I]

I have looked at my /etc/pam.d/common-auth, and am not sure where to put it. Gonna test it, see what happens.

Hmmm. There was already a try_first_pass, 
auth   [success=1 default=ignore]   pam_unix.se nullok_secure try_first_pass

Well, will keep on trying...

---

### Post by druhboruch on 2010-11-18
MyTer,
First try to do ldapsearch without -ZZ parameter.

You must get TLS working before you go to the next step.
SSSD will not work without it.

Try to ping and ssh to your ldap server by fqdn from the client to make sure that the computer name resolves correctly.

On the LDAP server the command hostname and hostname -f must return the same fqdn of your server and it must match the name in the certificate that you generated.
Check following files:
/etc/hosts
/etc/hostname

P.S. Don't forget to copy the certificate from your server to the client.

After that everything should work OK.

---

### Post by MyTer on 2010-11-18
Thanks a lot druhboruch

I could ping with fqdn (ldap.example.com), but not ssh to the server.

I edited /etc/hosts and /etc/hostname, 
using client.example.com instead of localhost.localdomain, 
and now i can ssh to the server and ldapsearch without -ZZ works. (Doesn't work with -ZZ)

I installed ldap-auth-config before I read Your last post, thought it could change anything, but it didn't

Still trying!

---

### Post by druhboruch on 2010-11-18
Please, post your /etc/hosts and /etc/hostname from both server and the client
Could you ldapsearch with -ZZ on the server using fqdn?

---

### Post by MyTer on 2010-11-18
**On the server**
/etc/hosts
192.168.0.7     ldap.example.com
127.0.0.1       ldap.example.com  localhost
127.0.1.1       ldap

/etc/hostname
ldap.example.com

**On the client**
/etc/hosts
192.168.0.100   lnxclient.example.com
127.0.0.1       lnxclient.example.com  localhost
127.0.1.1       lnxclient

/etc/hostname
lnxclient.example.com

No, ldapsearch did not work with -ZZ on the server.

I use gdm on the client. When logging in with a user, for instance 
john.people.example.com
Can I just use that in the gdm box?
Or do I have to use uid=john,ou=people,dc=example,dc=com
Or can I use john.people and skip example.com (base)

I have looked for examples on logging in, but not found any yet.

Btw, there is no need for authenticating twice anymore :popcorn:

---

### Post by MyTer on 2010-11-18
> **druhboruch said:**
> 

P.S. Don't forget to copy the certificate from your server to the client.


oops!

The certificate, is it /etc/ssl/certs/cacert.pem ?

I found
[https://help.ubuntu.com/community/OpenSSL](https://help.ubuntu.com/community/OpenSSL)
but that seems to apply to openSSL and not Gnutls.

---

### Post by druhboruch on 2010-11-18
Your hosts files are not correct:

```
127.0.0.1	localhost.localdomain	localhost
192.168.1.1	ldap.example.com	ldap

```

You are correct about the certificate file.
It must be copied from the server to the client and permissions must be set exacly as the other certificates in this folder.

Fist try this on the server and make sure that TLS works:
If this doesn't work then nothing will.
```

#/etc/ldap/ldap.conf:

URI ldap://ldap.example.com/
TLS_CACERT /etc/ssl/certs/cacert.pem

```


ldapsearch -x -h ldap.example.com -ZZ -b dc=example,dc=com

Once it works on the server, run it on the client.

For the login just use the username:  john
It will be uid from your ldap server.
You can login from gdm or from the console.  The login process is exactly the same as the default.

Good luck

---

