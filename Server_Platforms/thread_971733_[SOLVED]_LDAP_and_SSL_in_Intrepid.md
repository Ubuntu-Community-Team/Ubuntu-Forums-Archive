---
title: "[SOLVED] LDAP and SSL in Intrepid"
date: 2008-11-05
forum: Server Platforms
---

### Post by Apfelmaennchen on 2008-11-05
Hi folks!

I am having a hard time trying to run slapd in conjunction with SSL.

I followed the instructions from [http://www.openldap.org/doc/admin24/tls.html](http://www.openldap.org/doc/admin24/tls.html) and end up with the following error:
```
main: TLS init def ctx failed: -64
```
My slapd.conf reads as follows:
```
TLSCACertificateFile /etc/ssl/CA/MyCA/cacert.pem
TLSCertificateFile /etc/apache2/certs/MyHost-cert.pem
TLSCertificateKeyFile /etc/apache2/certs/MyHost-key.pem
```
The host key and certificate are owned by openldap:www-data and have permissions 444 (certificate) and 440 (key), while the CA-certificate is owned by myUser:users, permissions 644.

I even added
```
/etc/ssl/CA/MyCA/cacert r,
/etc/apache2/certs/MyHost-* r,
```
to SLAPD's apparmor profile - but to no avail 

Anyone got any ideas what I am missing?

Slapd version is 2.4.11
Oh and: the same stuff works without any glitches on the slapd that ships with Mac OS X 10.5.5...

Thanks A LOT in advance
d

PS:
I have upgraded my system to intrepid yesterday after I've spent some hours on this #@?%§$%$ in hardy.

EDIT:
Turned out to actually be an issue with file access to the "TLSCertificateKey".
Ownership of the file was www-data:openldap with permissions 660. Before using the OWNER:GROUP way, I had an ACL in place, that granted read permissions to the openldap user.
Since that didn't work, I removed the file ACL and changed ownership to the values above. Now I encountered an error in syslog that was someow connected to ACLs.
What eventually did the trick was to copy the certificate and key, change ownership of the key to openldap:openldap with 660 amd make slapd use this new copy.
Additionally I had to comment out the "TLSCACertificateFile"-directive. Doesn't make a lot of sense to me but hey, at least it's working now...

---

