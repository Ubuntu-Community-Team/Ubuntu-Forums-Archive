---
title: "LDAP Authentication for Web Access"
date: 2011-08-26
forum: Server Platforms
---

### Post by venkman1080 on 2011-08-26
LDAP Authentication for Web Access

I am trying to build a LDAP server to allow access to the wireless network in conjunction with Meraki wireless access points. I am using Ubuntu 10.10 and trying to install OpenLDAP from their documentation but I keep running into the error "configure: error: MozNSS not found - please specify the location to the NSPR and NSS header files in CPPFLAGS and the location to the NSPR and NSS libraries in LDFLAGS (if not in the system location)" I have OpenSSL installed but I also got these when I ran ./configure 

checking openssl/ssl.h usability... no
checking openssl/ssl.h presence... no
checking for openssl/ssl.h... no
checking gnutls/gnutls.h usability... no
checking gnutls/gnutls.h presence... no
checking for gnutls/gnutls.h... no
checking nssutil.h usability... no
checking nssutil.h presence... no
checking for nssutil.h... no

Any suggestions?

---

### Post by byb3 on 2011-08-30
It looks like is trying to use secure communication through SSL/TLS and you don't have it installed.

Have you tried 

```
apt-get install openssl
```As a starter?

---

### Post by idr99 on 2011-11-20
have you tried ./configure --with-tls=openssl ?

---

### Post by Yannou on 2012-03-13
Hi there !

I have the same problem (same error message while using ./configure) and tried what you proposed ( --with-tls=openssl ), since I already have openssl installed. 
But this is what I got :

```
configure error could not locate tls ssl package openldap
```Any idea ?
I'll continue searching on the web meanwhile.

Thank you in advance !


@venkman1080 : did you manage to solve your problem ? And if yes, how ?

---

### Post by glyndon on 2012-03-16
Yannou.
Looks like you may have typed 'openldap' instead of "openssl" on the end of the command line, and its error shows that. 

FWIW, though, I just tried this with openssl, and got an error similar to the MozNSS one - headers/libs not found.

---

### Post by glyndon on 2012-03-16
what just now worked for me was this line:

env CPPFLAGS=-I/usr/include/nss\ -I/usr/include/nspr LDFLAGS=-L/usr/lib/x86_64-linux-gnu/nss ./configure --with-tls

---

### Post by paco699 on 2013-02-07
Hello!

The "-dev" packages contains headers to compile with these libs.

-To compile with "--with-tls=openssl"
```
apt-cache search openssl | grep dev
apt-get install libssl-dev

```-To compile with "--with-cyrus-sasl"
```
apt-cache search sasl | grep dev
apt-get install libsasl2-dev
```And, openldap compilation:
```
./configure --with-cyrus-sasl --with-tls=openssl
```Also you need
```
apt-cache search gnutls | grep dev
apt-get install libgnutls-dev
```

And i think also
```
apt-cache search libnss
apt-get install libnss3-dev

```This method avoid to compile openssl, cyrus-sasl, gnutls and libnss and to maintain them easily.

Have a good day. :D

---

