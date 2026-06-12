---
title: "ldap 11.04 natty tls configuration"
date: 2011-12-11
forum: Server Platforms
---

### Post by brianmills on 2011-12-11
Hi,

I'm trying to get LDAP over TLS working on Ubuntu 11.04. I have tried this a couple of times and this step has never failed me so I'm a bit perplexed as to what is wrong. 

Essentlially I get up to running the ldapmodify command and I recieve an error. 

```

$ sudo ldapmodify -Y EXTERNAL -H ldapi:///
SASL/EXTERNAL authentication started
SASL username: gidNumber=0+uidNumber=0,cn=peercred,cn=external,cn=auth
SASL SSF: 0
dn: cn=config
add: olcTLSSCACertificateFile
olcTLSCACertificateFile: /etc/ssl/certs/cacert.pem
ldapmodify: wrong attributeType at line 3, entry "cn=config"
$

```

I cant seem to find a reason for this. Note, I'm also not recieving a password prompt when I start this process (which a lot of the examples out there suggest I should). 

Any thoughts on why this is failing?

Note, I can query LDAP remotley on non TLS fine and I have no problem there. I just cant seem to get the config added so I can alter it to TLS secured LDAP.

---

### Post by MidSpeck on 2012-01-12
Looks like you have an extra "S" in your add: <attribute> line.

The reason it's not asking for a password is two-fold, you are connecting to ldapi:// and using the EXTERNAL mechanism to verify that you are root (through the sudo command).

You can set it up to have a username and password using olcRootDN and olcRootPW if you'd prefer to be able to edit the configuration from anywhere.

---

