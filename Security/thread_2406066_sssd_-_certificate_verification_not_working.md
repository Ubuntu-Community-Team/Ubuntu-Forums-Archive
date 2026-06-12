---
title: "sssd - certificate_verification not working"
date: 2018-11-15
forum: Security
---

### Post by shankha72113 on 2018-11-15
Hi Experts,

In Ubuntu I am using sssd to let user login through OpenLDAP Server. Users are trying to login to the sssd client using ssh and sssd in tern sending the user's credential to OpenLDAP. The OpenLDAP server is working fine and as expected the TLS / SSL handshaking is taking place. 

Now, I want to implement certificate_verification as mentioned in the given link [http://manpages.ubuntu.com/manpages/cosmic/en/man5/sssd.conf.5.htm]("http://manpages.ubuntu.com/manpages/cosmic/en/man5/sssd.conf.5.html")l.

I have mentioned the sssd section the required parameter for certificate verification as follows.

[sssd]
certificate_verification = ocsp_default_responder=http://<OCSP URL>:8080/ocsp, ocsp_default_responder_signing_cert=<SIGNING CERTIFICATE NAME>

But, when I try to login through ssh to this sssd client vm, no traffic is generated  towards the OCSP server to validate the certificate being exchanged with the OpenLDAP server.

Will highly appreciate any valuable guidance from your side.

Regards,

---

