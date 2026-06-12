---
title: "OpenLDAP setup fails in Ubuntu 10.10 (Maverick)"
date: 2010-10-12
forum: Server Platforms
---

### Post by TrevorCampbell on 2010-10-12
I have just upgraded to Ubuntu 10.10 (Maverick Meerkat ) and can't install OpenLDAP successfully.  I am following the official documentation, (which is only up to date for 10.4) at [https://help.ubuntu.com/10.04/serverguide/C/openldap-server.html](https://help.ubuntu.com/10.04/serverguide/C/openldap-server.html)

I get up to loading the      backend.example.com.ldif but this fails as follows

[FONT=Courier New]$ sudo ldapadd -Y EXTERNAL -H ldapi:/// -f backend.example.com.ldif
SASL/EXTERNAL authentication started
SASL username: gidNumber=0+uidNumber=0,cn=peercred,cn=external,cn=auth
SASL SSF: 0
adding new entry "cn=module,cn=config"
ldap_add: Other (e.g., implementation specific) error (80)
    additional info: <olcModuleLoad> handler exited with 1



[/FONT]

---

### Post by randystech on 2010-10-17
I have the same problem. i have been unable to resolve this. The tutorial referenced works on 10.04 but not 10.10

---

### Post by aatlas on 2010-10-18
Please update documentation to 10.10 version or at least provide a solution...
Really blocking issue to create handy LDAP server...

---

### Post by martynbristow on 2010-10-18
Hey
I'm no Linux expert
But I am getting good at troubleshooting

I was using LDAP fine until an update a few months ago destroyed my LDAP config and I couldn't fix it

I have just loaded 10.10 Maverick

1) Ran apt-get install slapd ldap-utils
Nothing happend, it supposed to launch the wizard
2) Running at this minute dpkg-reconfigure slapd
This should give you the settings, don't know if it will work but im trying it
could someone advise please

---

### Post by martynbristow on 2010-10-18
Ok
that does'nt do very much
It still doesn't give you the options as before

---

### Post by m.kristian on 2010-10-19
commenting out this line will help:
#olcModuleload: back_hdb

---

### Post by jacobsallan on 2010-10-22
Got it. Adding an extension to the filename value fixes the LDIF file used to load database modules (backend.example.com.ldif).

% cat backend.dlinkddns.com.ldif
# Load dynamic backend modules
dn: cn=module,cn=config
objectClass: olcModuleList
cn: module
olcModulepath: /usr/lib/ldap
olcModuleload: back_hdb.la
...

There is still a problem with frontend.example.com.ldif; it seems to be either attempting to reload an entry for 'dc=example,dc=com' or to be invalid.  The existence of the node is confirmed by using the ldapsearch utility to list nodes.

% ldapsearch -x -b '' -s base '(objectclass=*)' namingContexts
# extended LDIF
#
# LDAPv3
# base <> with scope baseObject
# filter: (objectclass=*)
# requesting: namingContexts 
#
#
dn:
namingContexts: dc=dlinkddns,dc=com
# search result
search: 2
result: 0 Success
# numResponses: 2
# numEntries: 1

My guess is that the front end LDIF should start with something like

# Create top-level object in domain
dn: ou=orgs,dc=example,dc=com
objectClass: top
objectClass: dcObject
objectclass: organizationalUnit
ou: orgs

dn: o=Example Organization,ou=orgs,dc=example,dc=com
objectClass: organization
o: Example Organization

o: Example Organization
description: LDAP Example

---

### Post by jacobsallan on 2010-10-22
Done. Comment out 'dc: Example' in frontend.example.com.ldif and the LDAP database will be populated with the contents of that LDIF file.

# Create top-level object in domain
dn: dc=dlinkddns,dc=com
objectClass: top
objectClass: dcObject
objectclass: organization
o: Example Organization
#dc: Example
description: LDAP Example

---

### Post by aatlas on 2010-10-25
Still same error, even after commenting out "#olcModuleload: back_hdb"

adding new entry "olcDatabase=hdb,cn=config"
ldap_add: Other (e.g., implementation specific) error (80)
    additional info: <olcDbIndex> failed startup


Any clues ?

---

### Post by jacobsallan on 2010-10-26
Don't comment out "#olcModuleload: back_hdb".  Use "oldModuleload: back_hdb.la"
instead.

Allan Jacobs

---

### Post by jacobsallan on 2010-10-26
Continuing with the 10.04 server guide...

It looks like the line reading
"ldapsearch -xLLL -b cn=config -D cn=admin,cn=config -W olcDatabase=hdb olcAccess"
does not work.  OpenLDAP documentation recommends the use of "slapacl" tool to test access control settings.

Step #7 in the section "TLS and SSL" reads
sudo certtool --generate-certificate \
 --load-privkey /etc/ssl/private/x01-test_slapd_key.pem \
 --load-ca-certificate /etc/ssl/certs/cacert.pem \
 --load-ca-privkey /etc/ssl/private/cakey.pem \
 --template /etc/ssl/x01-test.info --outfile /etc/ssl/certs \
 /x01-test_slapd_cert.pem

Step #7, if it were to use names consistent with the previous steps would read
sudo certtool --generate-certificate \
 --load-privkey /etc/ssl/private/ldap01_slapd_key.pem \
 --load-ca-certificate /etc/ssl/certs/cacert.pem \
 --load-ca-privkey /etc/ssl/private/cakey.pem \
 --template /etc/ssl/ldap01.info --outfile /etc/ssl/certs \
 /ldap01_slapd_cert.pem

---

### Post by jacobsallan on 2010-10-27
The line in the 10.04 guide for OpenLDAP on Ubuntu reading
"ldapsearch -xLLL -b cn=config -D cn=admin,cn=config -W olcDatabase=hdb olcAccess"
was wrong.

Use
"ldapsearch -LLL -Y EXTERNAL -H ldapi:/// -b olcDatabase={1}hdb,cn=config olcAccess"
instead.

Has anyone checked the steps for replication?  I don't have the machinery.

Allan Jacobs

---

