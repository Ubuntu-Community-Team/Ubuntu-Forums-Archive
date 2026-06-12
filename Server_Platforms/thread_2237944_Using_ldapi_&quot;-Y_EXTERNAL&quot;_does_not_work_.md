---
title: "Using ldapi &quot;-Y EXTERNAL&quot; does not work any more after enabling TLS on openldap 2.4"
date: 2014-08-04
forum: Server Platforms
---

### Post by icicimov-gmail on 2014-08-04
I used the following LDIF file to activate the TLS support for the LDAP server:

dn: cn=config
changetype: modify
add: olcTLSCipherSuite
olcTLSCipherSuite: NORMAL 
-
add: olcTLSCRLCheck
olcTLSCRLCheck: none
-
add: olcTLSVerifyClient
olcTLSVerifyClient: never
-
add: olcTLSCACertificateFile
olcTLSCACertificateFile: /etc/ssl/certs/CA.crt
-
add: olcTLSCertificateFile
olcTLSCertificateFile: /etc/ssl/certs/server.pem
-
add: olcTLSCertificateKeyFile
olcTLSCertificateKeyFile: /etc/ssl/private/key.pem
and force the TLS usage for the client connections with the following LDIF:

dn: cn=config
changetype: modify
add: olcSecurity
olcSecurity: tls=1

After this I can't use the "-Y EXTERNAL" any more to read or modify the configuration schema. For example I get SASL error if I run:

$ sudo ldapsearch -Q -Y EXTERNAL -H ldapi:/// -b "" -LLL -s base -Z supportedSASLMechanisms
ldap_sasl_interactive_bind_s: Authentication method not supported (7)
    additional info: SASL(-4): no mechanism available: 

and if I check for supported SASL mechanisms:

$ sudo ldapsearch -x -H ldapi:/// -b "" -LLL -s base -Z supportedSASLMechanisms
dn:
supportedSASLMechanisms: DIGEST-MD5
supportedSASLMechanisms: CRAM-MD5
supportedSASLMechanisms: NTLM
supportedSASLMechanisms: PLAIN
supportedSASLMechanisms: LOGIN

I really can't see the EXTERNAL included in the list. What am I missing here?

This is on Ubuntu-12.04 and slapd-2.4.31.

---

