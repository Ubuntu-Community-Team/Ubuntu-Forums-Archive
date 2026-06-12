---
title: "slapd won't start after configuring TLS support"
date: 2012-12-26
forum: Server Platforms
---

### Post by herald on 2012-12-26
I've followed the instructions for installing and configuring OpenLDAP in the ubuntu server docs section.  I had the entire setup working beautifully in cleartext (tcp/389).  I then created a self signed certificate as described in the TLS section of the same documentation, exactly as posted there.  Now when I go to start the slapd service, the start fails, and the following is listed in the syslog file:

> Dec 26 20:59:30 janus slapd[1316]: @(#) $OpenLDAP: slapd  (Oct 17 2012 19:48:41) $#012#011buildd@komainu:/build/buildd/openldap-2.4.28/debian/build/servers/slapd
Dec 26 20:59:30 janus slapd[1316]: main: TLS init def ctx failed: -1
Dec 26 20:59:30 janus slapd[1316]: slapd stopped.

After much googling, I can infer that the -1 at the end of the middle line is a GNUTLS status message, but I can't find any of the documentation for GNUTLS that talks about their exception messages.

Can anyone point me to such documentation in GNUTLS, or has anyone seen this particular error?  Please note, this is not the -6x series that indicates access problems to the ca certificates.

the openldap user can access the cacert and the slapd cert just fine:

> root@janus:~# su - openldap -s /bin/bash -c 'openssl x509 -noout -subject -in /etc/ssl/certs/janus_slapd_cert.pem'
subject= /O=Short-e Systems/CN=janus.shortesys.net
root@janus:~# su - openldap -s /bin/bash -c 'openssl x509 -noout -subject -in /etc/ssl/certs/cacert.pem'
subject= /CN=Short-e Systems

Any suggestions are greatly appreciated!!

This is one of the last kinks I need to iron out before I move on to implementing kerberos with one time passwords, so it's killing me to be hung up on something so seemingly trivial!
Thanks!
-Herald

---

### Post by tmcneill on 2013-04-24
Herald - I'm having the exact same issue.  I've verified permission and location of certs and keys.  Once I add via ldapmodify

olcTLSCACertificateFile: /admin/sslCA/ca.jregw.local.cert
olcTLSCertificateFile: /etc/ssl/utl2.jregw.local.cert
olcTLSCertificateKeyFile: /etc/ssl/private/utl2.jregw.local.key

openldap blows up with 
517813a0 main: TLS init def ctx failed: -1
517813a0 slapd stopped.


Did you ever find a solution? 
Tom

---

### Post by tmcneill on 2013-04-24
I solved my problem.  The problem was apparmor.  It wasn't allowing openldap to access anything in /etc/ssl.  I discovered this because once I moved my keys and certs to /etc/ldap - openldap stopped blowing up with above error and started.

---

