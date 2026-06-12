---
title: "Vsftpd  and IBM zOS SSL error"
date: 2010-01-11
forum: Server Platforms
---

### Post by captflynt on 2010-01-11
After upgrading from Ubuntu 7.10 LTS server to 8.04.3 LTS a client connecting from an IBM FTP CS V1R9 client is unable to connect to the vsftpd server, version 2.0.6.  They were able to connect when running 7.10.  The vsftpd service is running with SSL enabled on port 21.  Here is the error they are getting:

EZA1701I >>> AUTH TLS
234 Proceed with negotiation.
FC0910 authServer: secure_socket_init failed with rc = 410 (SSL message format is incorrect)
EZA2897I Authentication negotiation failed
CZ0590 SETCEC code = 17
EZA2898I Unable to successfully negotiate required authentication                           

Any ideas?

Thanks.

---

### Post by jimbydamonk on 2010-04-14
I have lots of trouble with IBM SSL and Ubuntu. Here is what I think might be your problem. 

[http://publib.boulder.ibm.com/infocenter/lnxinfo/v3r0m0/index.jsp?topic=/liaai/kerberos/liaaikerbopenldap.htm](http://publib.boulder.ibm.com/infocenter/lnxinfo/v3r0m0/index.jsp?topic=/liaai/kerberos/liaaikerbopenldap.htm)

Basically GNU TLS is not playing nice. I have not found a way to replace GNU TLS with what is shipped with LDAP.

---

