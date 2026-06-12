---
title: "LDAP and SSL/TLS"
date: 2005-04-18
forum: Server Platforms
---

### Post by blueplazma on 2005-04-18
Ok.  I'm running OpenLDAP on a Hoary machine.  It works fine with the exception of SSL and TLS.  If I attempt to use either of them, anything involving authentication (I have Samba and PAM using LDAP) slows to a crawl.  When I attempted to test it with OpenSSL I get this:
```

admin@central:/etc/ldap$ sudo openssl s_client -connect localhost:389 -showcerts \ -state -CAfile /usr/lib/ssl/misc/demoCA/cacert.pem
CONNECTED(00000003)
SSL_connect:before/connect initialization
SSL_connect:SSLv2/v3 write client hello A
4071:error:140790E5:SSL routines:SSL23_WRITE:ssl handshake
failure:s23_lib.c:226:

```

I have no idea why this isn't working.  I made my own CA and signed the certificates.  I verified the certificates with said CA.  If anyone can tell me why this isn't working it would be great.

---

### Post by dataw0lf on 2005-04-18
Ensure that you have this in your slapd.conf

TLSCertificateFile <full path to slapd.pem>
TLSCertificateKeyFile <full path to slapd.pem>
 
And this line in your ldap.conf : 

TLS_CACERT <full path to slapd.pem>

---

### Post by speedman on 2005-04-18
Can you confirm that slapd is listening on port 636?

netstat -tupan|grep 636

I noticed you are trying to query localhost on port 389, which is typically not encrypted.

Will slapd allow you to query it over an encrypted connection?  For example using ldapsearch without the -x flag.


Regards,

SM


EDIT - fixed a typo.

---

### Post by blueplazma on 2005-04-18
[QUOTE=speedman]Can you confirm that slapd is listening on port 636?

netstat -tupan|grep 636

I noticed you are trying to query localhost on port 389, which is typically not encrypted.

Will slapd allow you to query it over an encrypted connection?  For example using ldapsearch without the -x flag.


Regards,

SM


EDIT - fixed a typo.[/QUOTE]

I'm trying to do TLS, not the older LDAPv2 SSL connection.  Slapd works fine, except for the encryption.  If I turn on encryption everything slows to a crawl.

---

### Post by blueplazma on 2005-04-18
[QUOTE=dataw0lf]Ensure that you have this in your slapd.conf

TLSCertificateFile <full path to slapd.pem>
TLSCertificateKeyFile <full path to slapd.pem>
 
And this line in your ldap.conf : 

TLS_CACERT <full path to slapd.pem>[/QUOTE]

I have all those lines, although it is possible that they are not correct.  You only use one filename (slapd.pem) - I have been generating slapd_key.pem and slapd_cert.pem.  In the TLS_CACERT line I have been putting the in the path to my certificate authority's certificate (/usr/lib/ssl/misc/demoCA/cacert.pem).  I tried doing it your way, and slapd refused to start.  Perhaps I misunderstood your instructions?

---

### Post by speedman on 2005-04-18
Here is the process I go through when building an LDAP server and putting self generated certs in place:

mkdir /tmp/certs

cd /tmp/certs

openssl req -new -nodes -out req.pem -keyout key.pem

openssl rsa -in key.pem -out new.key.pem

openssl x509 -in req.pem -out ca-cert -req -signkey new.key.pem -days 9999

mv new.key.pem server.pem

cat ca-cert >> server.pem

mkdir /etc/ldap/tls/

mv server.pem /etc/ldap/tls/

rm -fr /tmp/certs

The relevant entries to /etc/ldap/slapd.conf are:

TLSCACertificateFile    /etc/ldap/tls/server.pem
TLSCertificateFile      /etc/ldap/tls/server.pem
TLSCertificateKeyFile   /etc/ldap/tls/server.pem

HTH


Regards,

SM

---

### Post by blueplazma on 2005-04-19
I played around with it some more, and I figured out what I think is part of the problem.  Most of the apps I'm using don't know the CA (my own) that I used to sign the server's certificate.  So they all freeze up for some reason.  Could anyone tell me how to make the CA trusted on these machines so I can see if that was actually the problem?

---

### Post by speedman on 2005-04-19
Many applications - such as Evolution and Thunderbird - will prompt the user to accept the cert upon first connection and no further action is required.

For more information on LDAP and Samba integration I would suggest looking here:

[http://hannibal.solstice.nl/version-2.0/on_debian/hannibal-3.0_on-debian-sarge_2004-03-30.html](http://hannibal.solstice.nl/version-2.0/on_debian/hannibal-3.0_on-debian-sarge_2004-03-30.html)


Regards,

SM

---

### Post by blueplazma on 2005-04-19
[QUOTE=speedman]Many applications - such as Evolution and Thunderbird - will prompt the user to accept the cert upon first connection and no further action is required.

For more information on LDAP and Samba integration I would suggest looking here:

[http://hannibal.solstice.nl/version-2.0/on_debian/hannibal-3.0_on-debian-sarge_2004-03-30.html]("http://hannibal.solstice.nl/version-2.0/on_debian/hannibal-3.0_on-debian-sarge_2004-03-30.html")


Regards,

SM[/QUOTE]

I've got Thunderbird working with the SSL on. I just tell it permanently accept the CA and it's fine. The problem is on the servers I have connecting. They obviously do not run a mail client like Thunderbird or Evolution. Is it even an issue for them? Can I tell them to trust the CA like I tell Evolution/Thunderbird to?

EDIT: Thank you so much for that link.  I didn't know about the /etc/nss-ldap.conf file... I had only been changing /etc/ldap/ldap.conf, /etc/nsswitch.conf, and /etc/pam_ldap.conf.  In addition, I figured out that you need to copy the CA's certificate (for me it was /usr/lib/ssl/misc/demoCA/cacert.pem) to the client machines.  Then I needed to add the directive 
```

tls_cacert <full path to cacert.pem you copied>

```
to my /etc/ldap/ldap.conf file, as well as the other files I mentioned.  Thank you for your help.

---

### Post by speedman on 2005-04-19
[QUOTE=blueplazma]The problem is on the servers I have connecting.  They obviously do not run a mail client like Thunderbird or Evolution.  Is it even an issue for them?  Can I tell them to trust the CA like I tell Evolution/Thunderbird to?[/QUOTE]

What applications/services are you connecting with from the other servers?


Regards,

SM

---

### Post by blueplazma on 2005-04-19
[QUOTE=speedman]What applications/services are you connecting with from the other servers?


Regards,

SM[/QUOTE]

I was using GQ to edit the directory.  But if you look above, I've got it sorted out.  Thank you.

---

### Post by speedman on 2005-04-19
Good deal.  :) 

The Hannibal docs are a great resource.


Regards,

SM

---

### Post by blueplazma on 2005-04-19
[QUOTE=speedman]Good deal.  :) 

The Hannibal docs are a great resource.


Regards,

SM[/QUOTE]

They really are.  I never realized that extra file was there.

---

### Post by blueplazma on 2005-04-21
Alright.  I'm back.  I thought I had this problem cleared up, but I don't.  I've basically given up on TLS and I'm using the older ldaps:/// method.  It works reliably, unlike TLS which managed to crash the entire server every time it makes a search.  My only problem is that SSL takes a while to work.  I takes maybe twice as long as a regular unencrypted link takes to run a search.  I'm able to login, use ldapsearch, etc over the SSL encrypted connection, it's just slow.  Anyone else have this experience and/or any advice?  The server has plenty of memory and CPU power, so I know it isn't that.  Any help would be great.

---

### Post by sjansen on 2005-04-23
Confirmed. I'm using Ubuntu 5.04 and trying to get StartTLS over 389 working. I've done this many times before on other distros and never had a single problem, but always with OpenLDAP 2.2.X. Not sure if the problem is the patched gnutls, the old openldap, or a combination. Have you made any progress? I'm going to try to do a little more research and bugzilla.

---

### Post by blueplazma on 2005-04-23
[QUOTE=sjansen]Confirmed. I'm using Ubuntu 5.04 and trying to get StartTLS over 389 working. I've done this many times before on other distros and never had a single problem, but always with OpenLDAP 2.2.X. Not sure if the problem is the patched gnutls, the old openldap, or a combination. Have you made any progress? I'm going to try to do a little more research and bugzilla.[/QUOTE]

To be honest with you, I've managed to workaround by using ldaps:/// on port 636.  I've looked at countless debugs and countless logs to no avail.  There isn't even an error message unique to this TLS error.  My clients give a connect error, but nothing else.  There's nothing logged by slapd.  It just crashes, hard.  I'm thinking of submitting a bug report.

---

### Post by sjansen on 2005-04-23
Odd. I've just finished 45 minutes of carefully debugging. After beating it with enough strace's, the problem simply disappeared. I now have OpenLDAP running on 389, using StartTLS, working with Evolution and the speed is fine. At this point, I'm thinking race condition. Here's hoping it never returns.

---

### Post by blueplazma on 2005-04-23
Hooray for random fixes!  I'm glad it works for somebody.

---

