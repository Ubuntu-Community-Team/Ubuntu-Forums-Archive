---
title: "Problems with git and SSL"
date: 2011-10-20
forum: Security
---

### Post by BradNeuman on 2011-10-20
A bit of background:

I have spent a long time trying to understand this problem, with no luck, so hopefully someone here can enlighten me.

I am running a simple webserver which will host git repositories. We want to use smart http to allow git over https with autentication. Many of the people who will use these repositories are not very technically savvy, so we need a simple way for them to access the repos. Walking them through anything that requires any understand of using the command line aside from copy-pasting commands would be a huge headache, so we are hoping to avoid using ssh keys.

The problem:

I have a signed ssl certificate on the webserver which works in chrome and firefox, as well as using curl or wget with no errors or warnings, but when I go to check out a git repo ```
https://user@mysite.com/git/test.git
```, there is an error:

```
error: server certificate verification failed. CAfile: /etc/ssl/certs/ca-certificates.crt CRLfile: none
```

Now I think the problem is that for whatever reason, the CA certificate I am using (Comodo High-Assurance Secure Server CA) is not in the /etc/ssl/certs/ca-certificates.crt file, but rather is in one of the other files in /etc/ssl/certs. I suspect this because of the following verbose output from curl (with some of the personal info changed):

```

$ curl -v https://mysite.com
* About to connect() to mysite.com port 443 (#0)
*   Trying 127.0.0.1... connected
* Connected to mysite.com (127.0.0.1) port 443 (#0)
* successfully set certificate verify locations:
*   CAfile: none
  CApath: /etc/ssl/certs
* SSLv3, TLS handshake, Client hello (1):
* SSLv3, TLS handshake, Server hello (2):
* SSLv3, TLS handshake, CERT (11):
* SSLv3, TLS handshake, Server key exchange (12):
* SSLv3, TLS handshake, Server finished (14):
* SSLv3, TLS handshake, Client key exchange (16):
* SSLv3, TLS change cipher, Client hello (1):
* SSLv3, TLS handshake, Finished (20):
* SSLv3, TLS change cipher, Client hello (1):
* SSLv3, TLS handshake, Finished (20):
* SSL connection using DHE-RSA-AES256-SHA
* Server certificate:
*        subject: C=US; <... cut my certs info ...>
*        start date: 2011-10-18 00:00:00 GMT
*        expire date: 2013-10-17 23:59:59 GMT
*        subjectAltName: mysite.com matched
*        issuer: C=GB; ST=Greater Manchester; L=Salford; O=COMODO CA Limited; CN=COMODO High-Assurance Secure Server CA
*        SSL certificate verify ok.
> GET / HTTP/1.1
> User-Agent: curl/7.21.6 (x86_64-pc-linux-gnu) libcurl/7.21.6 OpenSSL/1.0.0e zlib/1.2.3.4 libidn/1.22 librtmp/2.3
> Host: mysite.com
> Accept: */*
>
< HTTP/1.1 200 OK
< Date: Tue, 18 Oct 2011 21:39:54 GMT
< Server: Apache/2.2.14 (Ubuntu)
< Last-Modified: Fri, 14 Oct 2011 03:20:01 GMT
< ETag: "8209c-87-4af39bb89ccac"
< Accept-Ranges: bytes
< Content-Length: 135
< Vary: Accept-Encoding
< Content-Type: text/html
< X-Pad: avoid browser bug
<
<p>Welcome to the mysite.com<p/>
* Connection #0 to host mysite.com left intact
* Closing connection #0
* SSLv3, TLS alert, Client hello (1):

```

Note that in the above curl output, CAfile is none and there is instead a CApath. Below is the verbose output from git:

```

$ GIT_CURL_VERBOSE=1 git clone https://mysite.com/test.git
Initialized empty Git repository in /home/maxlab/test/test2/.git/
* Couldn't find host mysite.com in the .netrc file; using defaults
* About to connect() to mysite.com port 443 (#0)
*   Trying 127.0.0.1... * connected
* Connected to mysite.com (127.0.0.1) port 443 (#0)
* found 141 certificates in /etc/ssl/certs/ca-certificates.crt
* server certificate verification failed. CAfile: /etc/ssl/certs/ca-certificates.crt CRLfile: none
* Expire cleared
* Closing connection #0
* Couldn't find host mysite.com in the .netrc file; using defaults
* About to connect() to mysite.com port 443 (#0)
*   Trying 127.0.0.1... * connected
* Connected to mysite.com (127.0.0.1) port 443 (#0)
* found 141 certificates in /etc/ssl/certs/ca-certificates.crt
* server certificate verification failed. CAfile: /etc/ssl/certs/ca-certificates.crt CRLfile: none
* Expire cleared
* Closing connection #0
error: server certificate verification failed. CAfile: /etc/ssl/certs/ca-certificates.crt CRLfile: none while accessing htt\
ps://mysite.com/test.git/info/refs

```

Now my questions are:

1. Why is git (which uses curl) using an explicit CA file, while curl by itself uses a CApath?

2. How can I convince git to use the CA path instead of the file?

3. Is there something else I'm not understanding? Should all the certs be in the /etc/ssl/certs/ca-certificates.crt file?

For 2 I have tried setting GIT_SSL_CAPATH but it seems to be ignored and gives me the exact same output as above. I've also tried clearing the CAfile by setting GIT_SSL_CAINFO='' but that just throws an error about not being able to open the CA file. I think that for some reason, git is ignoring the CAPATH and just using the file.

Pulling from git doesn't work on any version of ubuntu I've tried (10.04, 11.01 and 11.10), even from the webserver itself (running ubuntu 10.04), but it does work from an externally managed server which seems to be using NSS. Also, pulling and pushing using http both work.

I really hope someone here can help me out. I'd rather not turn off ssl verification in git, although that is a current workaround. Thanks for reading!

---

### Post by BradNeuman on 2011-10-27
After hours of head scratching I finally figured out this issue. It turns out that git on ubuntu uses gnutls instead of openssl, and git was the only thing using gnutls. The issue was that gnutls cares which order the intermediate certificates are in, so I swapped the order and everything started working

---

### Post by ssjp on 2011-11-03
I'm having the same problem using git. However, I don't know GnuTLS. How do I set the certificates in the right order? Is the reordering necessary on the server or on the client?   Thanks!

---

### Post by BradNeuman on 2011-11-04
I fixed the problem on the server. I had an intermediate certificate chain file, which I opened and just manually swapped the order (the file contained two certs).

I'm not sure how to fix this problem if you don't have access to the server, but to test if this is the issue you can install gnutls-bin and ```
run gnutls-cli -p 443 example.com
``` and see if you get an error (replace example.com with the server you are trying to connect to)

---

### Post by ssjp on 2011-11-04
Thank you for your answer! I tried gnutls and it gave no error message. Here is the output of gnutls-cli -p 443 host:
```
 - Ephemeral Diffie-Hellman parameters
- Using prime: 1024 bits 
- Secret key: 1022 bits
- Peer's public key: 1023 bits
- Certificate type: X.509
- Got a certificate list of 1 certificates. 
- Certificate[0] info: 
- subject ...
- The hostname in the certificate matches '...'.
- Peer's certificate issuer is unknown
- Peer's certificate is NOT trusted
- Version: TLS1.0
- Key Exchange: DHE-RSA
- Cipher: AES-128-CBC - MAC: SHA1
- Compression: NULL
- Handshake was completed
- Simple Client Mode: 
```

---

### Post by BradNeuman on 2011-11-04
hmmm, it looks like you are only getting one certificate. Unless you are a certificate authority (you're not), you should have more than one certificate. There should at least be 2, your certificate and the CA that signed it.

How did you get this certificate? This will only work if you either have a legitimate certificate signed by a CA, or you self-sign the certificate and install the certificate on each client you are trying to use.

CA signed certificates cost a lot of money, so unless you paid someone or got this through your company or something, its probably not signed by a CA.

---

### Post by ssjp on 2011-11-05
Ok, I understand (a bit more). :) The server is owned by my university. Is it right, that your proposal using a self-signed key only works, if I could replace the server certificate? Since I can not, is there a way to manually check the authenticity of the certificate and let gnutls remember this, so it will always accept this certificate?
I will also contact the administrator of my university and will see I he can help me. In the beginning, I just thought (since the output of git was the same for you and me), that I could use your way to solve the problem.

---

### Post by BradNeuman on 2011-11-06
I was administering my own server and my approach involved editing the certificate file on the server, so it doesn't sound like this would work for you. I'd definitely ask one of the university admins, they will probably know what the problem is.

Best of luck

---

### Post by mrengert on 2012-02-09
> **BradNeuman said:**
> I fixed the problem on the server. I had an intermediate certificate chain file, which I opened and just manually swapped the order (the file contained two certs).

I'm not sure how to fix this problem if you don't have access to the server, but to test if this is the issue you can install gnutls-bin and ```
run gnutls-cli -p 443 example.com
``` and see if you get an error (replace example.com with the server you are trying to connect to)


Hi -

I am seeing the same problem but with a well-known repository, namely jenkins-ci.org. I have Ubuntu 10.04 and when I use the gnutls-cli command, I see multiple certificates (although I note that the first one listed expired 2 days ago):
```

$ gnutls-cli -p 443 jenkins-ci.org
Resolving 'jenkins-ci.org'...
Connecting to '63.246.20.93:443'...
- Ephemeral Diffie-Hellman parameters
 - Using prime: 1024 bits
 - Secret key: 1023 bits
 - Peer's public key: 1024 bits
- Certificate type: X.509
 - Got a certificate list of 4 certificates.
 - Certificate[0] info:
  - subject `O=jenkins-ci.org,OU=Domain Control Validated,CN=jenkins-ci.org', issuer `C=US,ST=Arizona,L=Scottsdale,O=GoDaddy.com\, Inc.,OU=http://certificates.godaddy.com/repository,CN=Go Daddy Secure Certification Authority,serialNumber=07969287', RSA key 2048 bits, signed using RSA-SHA, activated `2011-02-18 00:48:14 UTC', expires `2012-02-07 00:37:49 UTC', SHA-1 fingerprint `502f96807238e120ae991b91728a3eb7693d00a6'
 - Certificate[1] info:
  - subject `C=US,ST=Arizona,L=Scottsdale,O=GoDaddy.com\, Inc.,OU=http://certificates.godaddy.com/repository,CN=Go Daddy Secure Certification Authority,serialNumber=07969287', issuer `C=US,O=The Go Daddy Group\, Inc.,OU=Go Daddy Class 2 Certification Authority', RSA key 2048 bits, signed using RSA-SHA, activated `2006-11-16 01:54:37 UTC', expires `2026-11-16 01:54:37 UTC', SHA-1 fingerprint `7c4656c3061f7f4c0d67b319a855f60ebc11fc44'
 - Certificate[2] info:
  - subject `C=US,O=The Go Daddy Group\, Inc.,OU=Go Daddy Class 2 Certification Authority', issuer `L=ValiCert Validation Network,O=ValiCert\, Inc.,OU=ValiCert Class 2 Policy Validation Authority,CN=http://www.valicert.com/,EMAIL=info@valicert.com', RSA key 2048 bits, signed using RSA-SHA, activated `2004-06-29 17:06:20 UTC', expires `2024-06-29 17:06:20 UTC', SHA-1 fingerprint `de70f4e2116f7fdce75f9d13012b7e687a3b2c62'
 - Certificate[3] info:
  - subject `L=ValiCert Validation Network,O=ValiCert\, Inc.,OU=ValiCert Class 2 Policy Validation Authority,CN=http://www.valicert.com/,EMAIL=info@valicert.com', issuer `L=ValiCert Validation Network,O=ValiCert\, Inc.,OU=ValiCert Class 2 Policy Validation Authority,CN=http://www.valicert.com/,EMAIL=info@valicert.com', RSA key 1024 bits, signed using RSA-SHA, activated `1999-06-26 00:19:54 UTC', expires `2019-06-26 00:19:54 UTC', SHA-1 fingerprint `317a2ad07f2b335ef5a1c34e4b57e8b7d8f1fca6'
- The hostname in the certificate matches 'jenkins-ci.org'.
- Peer's certificate issuer is unknown
- Peer's certificate is NOT trusted
- Version: TLS1.0
- Key Exchange: DHE-RSA
- Cipher: AES-128-CBC
- MAC: SHA1
- Compression: NULL
- Handshake was completed

- Simple Client Mode:

- Peer has closed the GNUTLS connection

```Is this a problem ad jenkins-ci.org or is there something wrong at my end? I have been able to use git to access several other well-known repositories in the past.

---

### Post by BradNeuman on 2012-02-13
> Is this a problem ad jenkins-ci.org or is there something wrong at my end? I have been able to use git to access several other well-known repositories in the past.

I can't say for sure but I'd guess it's the expired certificates. You should be able to get around it by allowing untrusted certs temporarily, but I'd ask someone over at  jenkins-ci.org at least to see if other people are seeing this problem

---

