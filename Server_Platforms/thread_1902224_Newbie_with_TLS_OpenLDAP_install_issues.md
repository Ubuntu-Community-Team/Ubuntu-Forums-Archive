---
title: "Newbie with TLS OpenLDAP install issues"
date: 2011-12-30
forum: Server Platforms
---

### Post by brodgers10 on 2011-12-30
I'm new at this, so be kind...  Yes, I've RTF and done numerous Google searches, but I still am having issues.

So, this is a new install of Ubuntu Server 11.04.  Everything has gone great in the basic install process.  I am now following the server guide for OpenLDAP installation:

[https://help.ubuntu.com/11.04/serverguide/C/openldap-server.html](https://help.ubuntu.com/11.04/serverguide/C/openldap-server.html)

I have made it through:
Populating LDAP - Fine
LDAP Replication - Skipped
Setting Up ACL - Fine
TLS and SSL - Here's where I am having issues.

I made it through Step 7 with no problems.  After Step 7 it says:
"Once you have a certificate, key, and CA cert installed, use **ldapmodify** to add the new            configuration options:           " and then gives a bunch of options.

How do I use this code (that was provided): 
[B]sudo ldapmodify -Y EXTERNAL -H ldapi:///

[FONT=Verdana]To add these changes (that were provided):[/FONT]
[/B]Enter LDAP Password: **dn: cn=config add: olcTLSCACertificateFile olcTLSCACertificateFile: /etc/ssl/certs/cacert.pem - add: olcTLSCertificateFile olcTLSCertificateFile: /etc/ssl/certs/ldap01_slapd_cert.pem - add: olcTLSCertificateKeyFile olcTLSCertificateKeyFile: /etc/ssl/private/ldap01_slapd_key.pem**  modifying entry "cn=config"
I feel like this should be easy and is just a basic lack of knowledge about how to use "ldapmodify", but I still need help.  So, please help me!!!

Thanks in advance,
Brad

---

### Post by devlam on 2012-01-09
Hello here a reply from a newbie too. I'm doing the same.
I figured out the following.
Firing the modify command will set you in input mode.
Although the manual shows "Enter LDAP Password:", no password is asked when I fire the command.
But I can copy/past te rest of the "statements". Don't paste the last line. This will show up if you put the white-line at the end as a close op input mode.

Nevertheless at the end my server responds with:
```
ldap_modify: Insufficient access (50)
```

All the reference files are in place and showing up with a sudo ls.

Someone an idea?

---

### Post by Merganser on 2012-01-09
I'm going through this on 10.04 and have spent plenty of time scrathing my head.  On thing that helped me was looking the 11.10 documentation for LDAP.  It has been updated and is much improved IMHO.  There is some added info, like the on disk layout of the database files and at least one corrected ldapmodify command.

The TLS section is better.  It wil have you add the cert information by creating a sript and loading it that way rather than from the command line.  if you stop slapd you can edit these settings in /etc/ldap/slapd.d/cn=config.ldif.  (you can probably edit with it running but that seems like a bad idea.  Also if slapd.d won't start after you add your certs you can remove the 3 cert settings and it should start gain.


One thing I will add is that I had difficutly with slapd being able to access my certs, even after given it read permissions.  Not sure why.  The solution that worked for me was to put the sever cert and private key in a "ssl" folder under /etc/ldsap.  The ca cert was fine in /etc/ssl/certs.  If slapd can't get to the certs it won't load and you'll need to edit /etc/ldap/slapd.d/cn=config.ldif as I mentioned above.

---

### Post by devlam on 2012-01-19
Okay I took some timeout but now I'm starting again. But now with the 11.10 documentation.

I don't know how to undo all the things I did so I'm trying if the things are in place.

Within the post-install inspection it first shows the directory-structure below /etc/ldap/slapd.d.

1. little issue (probably caused by beeing a newbee)
I can't go to that directory with the cd-command, it says permission denied.

ls -all on the /etc/ldap shows:
"drwxr-x--- 3 openldap openldap <size> <date> <time> slapd.d"

however
sudo ls /etc/ldap/slapd.d 
shows the content of slapd.d (it is the same structure as in the 11.10 documentation)

The openldap comes from the installation on the 10.04 which I started from a created directory openldap in my $HOME

2. sudo ldapsearch -Q -LLL -Y EXTERNAL -H ldapi:/// -b cn=config dn 
This gives the error "No such object (32).
Probably this is related to the permission denied from 1?

Please can someone help me out.

---

