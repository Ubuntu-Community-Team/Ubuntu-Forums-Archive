---
title: "ldap client doesn't know CA?!"
date: 2009-01-05
forum: Server Platforms
---

### Post by Niels Olson on 2009-01-05
Hello,

I'm working on an app server running Ubuntu 8.10 and we need secure ldap. Problem is the ldap client doesn't trust the ldap server's certificate because it believes the issuer of the certificate is unknown. But it is a very common CA: Equifax Secure Certificate Authority. I checked, and the Equifax Secure Certificate Authority pem file is loaded in /etc/ssl/certs. I fetched the cert and installed it again and ran c_rehash just to make sure.

Here's where I'm at in terms of debugging
```

mail /etc/ldap: ldapsearch -x -d5 -H ldaps://myldap.server.com
ldap_url_parse_ext(ldaps://myldap.server.com)
ldap_create
ldap_url_parse_ext(ldaps://myldap.server.com:636/??base)
ldap_sasl_bind
ldap_send_initial_request
ldap_new_connection 1 1 0
ldap_int_open_connection
ldap_connect_to_host: TCP myldap.server.com:636
ldap_new_socket: 3
ldap_prepare_socket: 3
ldap_connect_to_host: Trying 11.22.33.44:636
ldap_pvt_connect: fd: 3 tm: -1 async: 0
TLS: warning: cacertdir not implemented for gnutls
TLS: peer cert untrusted or revoked (0x42)
ldap_err2string
ldap_sasl_bind(SIMPLE): Can't contact LDAP server (-1)
```

and here's gnutls-cli
```

mail /etc/ldap: gnutls-cli --print-cert -p 636 ldap.server.com
Resolving 'ldap.server.com'...
Connecting to '11.22.33.44:636'...
- Certificate type: X.509
 - Got a certificate list of 1 certificates.

 - Certificate[0] info:

-----BEGIN CERTIFICATE-----
blah blah
-----END CERTIFICATE-----

 # The hostname in the certificate matches 'ldap.server.com'.
 # valid since: 
 # expires at: 
 # fingerprint: 
 # Subject's DN: C=US,ST=xxxx,L=xxxx,O=xxxx,OU=xxxx,CN=ldap.server.com
 # Issuer's DN: C=US,O=Equifax,OU=Equifax Secure Certificate Authority


- Peer's certificate issuer is unknown
- Peer's certificate is NOT trusted
- Version: TLS1.0
- Key Exchange: RSA
- Cipher: ARCFOUR-128
- MAC: MD5
- Compression: NULL
- Handshake was completed
```

If you caught the "cacertdir not implemented for gnutls", yes, I did have a tls_cacertdir specified in my ldap.conf, but when I take that out, I still get all the other errors. That seems to be irrelevant to the issue at hand.

---

### Post by Niels Olson on 2009-01-05
hmmmmm . . . this appears to have already been identified and elevated to a higher level than I:

[http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=507633](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=507633)
[https://bugs.launchpad.net/debian/+source/gnutls26/+bug/305264/](https://bugs.launchpad.net/debian/+source/gnutls26/+bug/305264/)
[http://lists.gnu.org/archive/html/gnutls-devel/2008-12/msg00016.html](http://lists.gnu.org/archive/html/gnutls-devel/2008-12/msg00016.html)

but, while I'm here, let me note some useful debugging commands if this should happen to you too:

openssl s_client -connect ldap.server.com:443 -CApath /etc/ssl/certs (this says everything works)

gnutls-cli --print-cert -p 636 ldap.server.com (this says it's broken)

gnutls-cli --x509cafile /etc/ssl/certs/Equifax_Secure_Certificate_Authority.cer -p 636 ldap.server.com (this says everything works)
 

ldapsearch -x -d5 -H ldaps://ldap.server.com (this says its broken)

ldapsearch -x -d3 -H ldaps://ldap.server.com (just a different debugging level, still says it's broken)

---

### Post by eescudier on 2009-02-02
Hi,

I think I am facing the same problem :
- new Ubuntu 8.10 server
- need to connect thru ldaps with an Active Directory
- using a self signed certificate (I added my CA to the ubuntu server)

It works on my old ubuntu 6.10 server (so on the windows side everything is ok), but I can't get it to work on the 8.10 box...
Below you'll find the errors.

What can I do ?

Thanks for any help

```

gnutls-cli -p 636 myADLDAPserver -d 1 --print-cert

Resolving 'myADLDAPserver '...
Connecting to '10.1.36.2:636'...
- Successfully sent 0 certificate(s) to server.
- Certificate type: X.509
 - Got a certificate list of 1 certificates.

 - Certificate[0] info:

-----BEGIN CERTIFICATE-----
blabla
-----END CERTIFICATE-----

 # The hostname in the certificate matches 'myADLDAPserver'.
 # valid since: Mon Feb  2 09:33:36 CET 2009
 # expires at: Wed Feb  2 09:33:36 CET 2011
 # fingerprint: XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX
 # Subject's DN: CN=myADLDAPserver
 # Issuer's DN: DC=XX,DC=XX,CN=XXXXXX


- Peer's certificate issuer is unknown
- Peer's certificate is NOT trusted
- Version: TLS1.0
- Key Exchange: RSA
- Cipher: ARCFOUR-128
- MAC: MD5
- Compression: NULL
- Handshake was completed

- Simple Client Mode:


```

and


```

ldapsearch -d5 -x -H "ldaps://myADLDAPserver/" -D "myUser" -b "dc=XX,dc=XXX" -W
ldap_url_parse_ext(ldaps://myADLDAPserver/)
ldap_create
ldap_url_parse_ext(ldaps://myADLDAPserver:636/??base)
Enter LDAP Password:
ldap_sasl_bind
ldap_send_initial_request
ldap_new_connection 1 1 0
ldap_int_open_connection
ldap_connect_to_host: TCP myADLDAPserver:636
ldap_new_socket: 3
ldap_prepare_socket: 3
ldap_connect_to_host: Trying 10.1.36.2:636
ldap_pvt_connect: fd: 3 tm: -1 async: 0
TLS: warning: cacertdir not implemented for gnutls
TLS: peer cert untrusted or revoked (0x42)
ldap_err2string
ldap_sasl_bind(SIMPLE): Can't contact LDAP server (-1)

```

---

### Post by Niels Olson on 2009-02-02
I got mine working, though I've forgotten some of the how to. Sorry.

Um... here's my entire, one line ldap.conf:

```
TLS_CACERT      /etc/ssl/certs/ca-certificates.crt
```

and it looks like I had to add these to my /etc/ssl/certs

Equifax_Secure_Certificate_Authority.cer
Equifax_Secure_Certificate_Authority_DER.cer

which can be downloaded from GeoTrust

[http://www.geotrust.com/resources/root-certificates/](http://www.geotrust.com/resources/root-certificates/)

but check, as they might already be in there.

I do recall it being amazingly simple once I got it figured out. I think the Ubuntu default ldap.conf is really set up more for you if you're also running your own ldap server, but that's honestly speculative on my part.

---

### Post by eescudier on 2009-02-03
> **Niels Olson said:**
> 
Um... here's my entire, one line ldap.conf:

```
TLS_CACERT      /etc/ssl/certs/ca-certificates.crt
```



This did the trick, with this ldap.conf everything works fine.
Thanks for your help.

Eric

---

