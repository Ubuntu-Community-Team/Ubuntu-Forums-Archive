---
title: "LDAP Installation Error Notes (10.04 LTS) Lucid Lynx"
date: 2011-08-12
forum: Server Platforms
---

### Post by Linux90's on 2011-08-12
If you are installing LDAP, you may have come across errors in your process:

The Install Procedure is here:
[https://help.ubuntu.com/10.04/serverguide/C/openldap-server.html](https://help.ubuntu.com/10.04/serverguide/C/openldap-server.html)


If you see the following error when you start to add TLS/SSL support:

olcTLSCACertificateFile: no equality matching rule


Go here ->

[https://help.ubuntu.com/10.04/serverguide/C/certificates-and-security.html](https://help.ubuntu.com/10.04/serverguide/C/certificates-and-security.html)


You need to do these:

1. Generate a Certificate Signing Request (CSR)
2. Create a Self-Signed Certificate
3. Installing the Certificate

Once you have done these, go over your TLS/SSL installation again and it should work just fine.

Ideally, do these BEFORE you begin adding TLS/SSL support as you will not see these errors. 

If you are stuck because of slapd, either purge it with

apt-get purge slapd 

or you can do 

dpkg-reconfigure slapd

Then do the cert work followed by Ldap

Good Luck

---

