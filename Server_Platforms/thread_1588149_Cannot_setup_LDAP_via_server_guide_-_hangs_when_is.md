---
title: "Cannot setup LDAP via server guide - hangs when issuing &quot;ldapmodify&quot; command"
date: 2010-10-04
forum: Server Platforms
---

### Post by daarkstaar on 2010-10-04
I have been trying to set up an LDAP server for a development environment as part of an internship for a week now, and I cannot get past this point.  I have been following the 10.04 server guide to set up LDAP here: 

[https://help.ubuntu.com/10.04/serverguide/C/openldap-server.html](https://help.ubuntu.com/10.04/serverguide/C/openldap-server.html)

Once I get to the following point in the guide, it just hangs:
 "As an example of modifying the cn=config tree, add another attribute to the index list using ldapmodify:"

sudo ldapmodify -Y EXTERNAL -H ldapi:///

After issuing the previous command I get this output:

SASL/EXTERNAL authentication started
SASL username: gidNumber=0+uidNumber=0,cn=peercred,cn=external,cn=auth
SASL SSF: 0

It stays here unless I issue a ctrl+D.

Here's the output from the syslog:

Oct  4 13:26:38 devLDAP slapd[2103]: @(#) $OpenLDAP: slapd 2.4.21 (Aug 10 2010 17:08:36) $#012#011buildd@yellow:/build/buildd/openldap-2.4.21/debian/build/servers/slapd
Oct  4 13:26:38 devLDAP slapd[2103]: daemon: bind(7) failed errno=13 (Permission denied)
Oct  4 13:26:38 devLDAP slapd[2103]: daemon: bind(7) failed errno=13 (Permission denied)
Oct  4 13:26:38 devLDAP slapd[2103]: slapd stopped.
Oct  4 13:26:38 devLDAP slapd[2103]: connections_destroy: nothing to destroy.

Can anyone help me figure what's going on here?  Like I stated earlier, I've been working on this for a week and can't understand why this won't work.  I am fairly certain that I've followed the guide to a 'T.'  Any idea why am I receiving a permission denied error?  Is this a permissions issue with one of the config files?

Any help would be greatly appreciated.

---

### Post by daarkstaar on 2010-10-05
Here's some more information -

After entering locations of keyfiles and CA, here's the output I get:

root@devLDAP:~# sudo ldapmodify -Y EXTERNAL -H ldapi:///
SASL/EXTERNAL authentication started
SASL username: gidNumber=0+uidNumber=0,cn=peercred,cn=external,cn=auth
SASL SSF: 0
dn: cn=config
add: olcTLSCACertificateFile
olcTLSCACertificateFile: /etc/ssl/certs/cacert.pem
-
add: olcTLSCertificateFile
olcTLSCertificateFile: /etc/ssl/certs/devLDAP_slapd_cert.pem
-
add: olcTLSCertificateKeyFile
olcTLSCertificateKeyFile: /etc/ssl/private/devLDAP_slapd_key.pem
modifying entry "cn=config"
ldap_modify: Insufficient access (50)


Can anyone tell me why I am getting "Insufficient access(50)" and "failed errno=13 (Permission Denied)"  errors?


EDIT:  The above is from section 7 in the guide, I am trying to set up TLS so I can integrate Kerberos with LDAP.  Point is, I cannot seem to use ldapmodify at all because of permission errors; what gives?

---

### Post by luvshines on 2010-10-05
Do we actually need to add the schema and indexing from command line ??
I thought it was directly controlled from slapd.conf :confused:

---

### Post by daarkstaar on 2010-10-05
From what I understand, with newer version of openLDAP, all configuration is done through cn=config and slapd.conf is no longer used.  When cn=config is edited, changes are updated automatically, without requiring a slapd restart.  Someone correct me if I'm wrong.

---

### Post by luvshines on 2010-10-05
Oh, is it ??
My bad, still Fedora & RHEL lingering in my mind. Haven't tried LDAP server on Ubuntu

I tried to install it and am stuck at the very first step. Atleast you are at better position :D

```

sudo apt-get install slapd
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  slapd: Depends: libldap-2.4-2 (= 2.4.21-0ubuntu5.2) but 2.4.21-0ubuntu5.3 is to be installed
E: Broken packages

```

---

### Post by daarkstaar on 2010-10-05
try this:

sudo apt-get update
sudo apt-get install slapd ldap-utils

---

### Post by luvshines on 2010-10-05
Nope!! That didn't help. Did an update and then a retry

```

sudo apt-get install slapd ldap-utils
Reading package lists... Done
Building dependency tree       
Reading state information... Done
ldap-utils is already the newest version.
ldap-utils set to manually installed.
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  slapd: Depends: libldap-2.4-2 (= 2.4.21-0ubuntu5.2) but 2.4.21-0ubuntu5.3 is to be installed
E: Broken packages

dpkg -l | grep libldap
ii  libldap-2.4-2                         2.4.21-0ubuntu5.3                               OpenLDAP libraries

```

Looks like it hates the 5.3 installed and is demanding 5.2

Can you check what libldap is installed on urs ?

---

### Post by daarkstaar on 2010-10-05
I've got 5.3 also:

user1@devLDAP:/etc/ldap$ dpkg -l | grep libldap
ii  libldap-2.4-2          2.4.21-0ubuntu5.3                              
OpenLDAP libraries

---

### Post by daarkstaar on 2010-10-06
I still can't figure out why I can't modify anything with ldapmodify.  Here's the ACL:

user1@devLDAP:~$ ldapsearch -xLLL -b cn=config -D cn=admin,cn=config -W olcDatabase=hdb olcAccess
Enter LDAP Password:
dn: olcDatabase={1}hdb,cn=config
olcAccess: {0}to attrs=userPassword,shadowLastChange by dn="cn=admin,dc=VeraxI
 D,dc=local" write by anonymous auth by self write by * none
olcAccess: {1}to dn.base="" by * read
olcAccess: {2}to * by dn="cn=admin,dc=VeraxID,dc=local" write by * read


Is there something wrong above that might be denying me access?

I could really use someone's help with this!

---

### Post by luvshines on 2010-10-06
Did you try ldapmodify with -x -D <admin-dn> -W instead of -Y EXTERNAL ?

---

### Post by daarkstaar on 2010-10-06
Thanks for the reply.  I just tried that and got this error:

user1@devLDAP:/usr/local/scripts$ sudo ldapmodify -x -D cn=admin,dc=VeraxID,dc=local -W
Enter LDAP Password:
dn: cn=config
add: olcTLSCACertificateFile
olcTLSCACertificateFile: /etc/ssl/certs/cacert.pem
-
modifying entry "cn=config"
ldap_modify: Insufficient access (50)

I must be making a really stupid mistake somewhere, but for the life of me, I don't know where. :(

---

### Post by luvshines on 2010-10-06
Does slapd -Ta also fails with same error ?

---

### Post by druhboruch on 2010-10-06
This is a howto that worked for me on Maverick RC server:
[http://albanianwizard.org/ubuntu-10-0-4-lucid-lynx-ldap-configuration-the-working-how-to.albanianwizard](http://albanianwizard.org/ubuntu-10-0-4-lucid-lynx-ldap-configuration-the-working-how-to.albanianwizard)

---

### Post by daarkstaar on 2010-10-06
Thanks for the replies guys :)

luvshines -

after issuing slapd -Ta i get this error:

ldif_read_file: Permission denied for "/etc/ldap/slapd.d/cn=config.ldif"
slapadd: bad configuration file!

but when run as root, I get:

root@devLDAP:/etc# slapd -Ta
hdb_db_open: database "dc=VeraxID,dc=local": database already in use.
backend_startup_one (type=hdb, suffix="dc=VeraxID,dc=local"): bi_db_open failed! (-1)
slap_startup failed


druhboruch - 

I've used the same script from here:  [http://www.ghacks.net/2010/08/31/set-up-your-ldap-server-on-ubuntu-10-04/](http://www.ghacks.net/2010/08/31/set-up-your-ldap-server-on-ubuntu-10-04/)

It set up a working LDAP, but when trying to setup TLS, I ran into the same permission denied errors when trying to add certs and keys to the config.


Here's a question.  The slapd.d directory is owned by openldap, is this causing me permission issues when using ldapmodify since I run the command as root?  I've tried sudo -u openldap ldapmodify ... but it asks for a password and I don't know what it is for that user.  Sorry if I'm confused here, I'm still learning the ropes.

EDIT:  Also, I can only access the slapd.d directory as root (sudo su), could this be causing me issues?

---

### Post by druhboruch on 2010-10-06
You can add the keys after installation of slapd, just before you run the script.
In fact generating and installing certificates is the first thing to do.
Use ldapadd -Y EXTERNAL

If you want to do it later than you should remove from the script following:

```
dn: olcDatabase={0}config,cn=config
changetype: modify
delete: olcAccess
```

It should work.

You can optionally delete oldAccess after everything works ok.

---

### Post by daarkstaar on 2010-10-06
Thanks Druh, I'll give it a shot tomorrow and post results.

---

### Post by daarkstaar on 2010-10-07
druhboruch - 

Thanks a million for the tip!  I was able to add the certs using "ldapmodify" instead of "ldapadd" before running the script.  Another question, is this code preventing me from modifying the config after I run the script?

```
dn: olcDatabase={0}config,cn=config
changetype: modify
delete: olcAccess
```

  I.e., will this prevent me from using ldapmodify to alter the config later on?  If so, how can I avoid that issue?

Thanks again, you've saved me a ton of frustration! :)

---

### Post by druhboruch on 2010-10-07
I think that once removed the config is sealed.

Maybe somebody else experienced with ldap could answer this.

In the meantime we will wait for the updated server guide...

---

### Post by kaouacherif on 2011-03-22
Hello
i'm on debian sequeeze 6.0 and was getting the same error 50

using this worked directly without any change :


**ldapmodify -Y EXTERNAL -H ldapi:///**


and didn't prompt for password ^^


i used it with this entry

dn: cn=config
add: olcTLSCACertificateFile
olcTLSCACertificateFile: /etc/ldap/ssl/server.pem
-
add: olcTLSCertificateFile
olcTLSCertificateFile: /etc/ldap/ssl/server.pem
-
add: olcTLSCertificateKeyFile
olcTLSCertificateKeyFile: /etc/ldap/ssl/server.pem


Hope i helped you all.

Regards 

Cherif Kaoua from Algeria

---

### Post by kaouacherif on 2011-03-22
here is the best tutorial i found

[https://help.ubuntu.com/9.10/serverguide/C/openldap-server.html]("https://help.ubuntu.com/9.10/serverguide/C/openldap-server.html")

and you will find an other link in the middle of this tutorial only about generating certificate just "copy past " and read carefully 
it's perfect

here is the 2nd link about certificate

[https://help.ubuntu.com/9.10/serverguide/C/certificates-and-security.html]("https://help.ubuntu.com/9.10/serverguide/C/certificates-and-security.html")


weeks and weeks trying to start LDAP on ssl 
and finally i done it 

If you have any question just ask here

hope i helpd everyone
have fun 


Regards

Cherif Kaoua from Algeria

---

