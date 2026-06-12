---
title: "GnuTLS: certtool never asks for CA-password when signing certificates (12.04 server)"
date: 2012-06-20
forum: Security
---

### Post by Shilong on 2012-06-20
Hi forum

I have created a GnuTLS CA and would like to sign my server certificates with it.

```
[root@host] certtool -v
certtool (GnuTLS) 2.12.14
(...)
```

1. Create a private key for the CA:

```
[root@host] certtool --generate-privkey --outfile ca_tls.key --password "secret"
(...)
```

2. Create a self-signed certificate for the CA

```
[root@host] certtool --generate-self-signed --load-privkey ca_tls.key --outfile ca_tls.cert --password "secret"
Generating a self signed certificate...
Please enter the details of the certificate's distinguished name. Just press enter to ignore a field.
(...)
Does the certificate belong to an authority? (y/N): y
Path length constraint (decimal, -1 for no constraint): -1
Is this a TLS web client certificate? (y/N): n
Will the certificate be used for IPsec IKE operations? (y/N): 
Is this also a TLS web server certificate? (y/N): n
Enter the e-mail of the subject of the certificate: 
Will the certificate be used to sign other certificates? (y/N): y
Will the certificate be used to sign CRLs? (y/N): y
Will the certificate be used to sign code? (y/N): y
Will the certificate be used to sign OCSP requests? (y/N): y
(...)
```

3. Create a key for the server

```
[root@host] certtool --generate-privkey --outfile server_tls.key
```

4. Create a certificate for the server

```
[root@host] certtool --generate-certificate --load-privkey server_tls.key --load-ca-certificate ca_tls.cert --load-ca-privkey ca_tls.key --outfile server_tls.cert
Generating a signed certificate...
Please enter the details of the certificate's distinguished name. Just press enter to ignore a field.
(...)
Does the certificate belong to an authority? (y/N): 
Is this a TLS web client certificate? (y/N): 
Will the certificate be used for IPsec IKE operations? (y/N): 
Is this also a TLS web server certificate? (y/N): y
Enter a dnsName of the subject of the certificate: server
Enter a dnsName of the subject of the certificate: server.com
Enter a dnsName of the subject of the certificate: www.server.com
Enter a dnsName of the subject of the certificate: 
Enter the IP address of the subject of the certificate: 
Will the certificate be used for signing (DHE and RSA-EXPORT ciphersuites)? (y/N): 
Will the certificate be used for encryption (RSA ciphersuites)? (y/N): y
(...)
Is the above information ok? (y/N): y


Signing certificate...
```

The certificate for the server gets created and works fine - e.g. with apache. However, I would expect to be asked for the CA password (created in step1) when signing the certificate in step 4. This doesn't happen.

Therefore my questions:
[LIST]
[*]Why doesn't certtool ask for the CA password when signing a new certificate? 
[LIST]
[*]In other words: What's the point of defining a password when I never have to enter it again?
[/LIST]
[*]Why can I even define a password for the CA certificate in step 2?
[LIST]
[*]I would think a password for the CA key should be sufficient?
[/LIST]
[/LIST]

Thanks in advance
Shilong

---

### Post by Shilong on 2012-06-30
I have posted the same question in the german board, so far without any answer either:

[http://forum.ubuntuusers.de/topic/gnutls-certtool-fragt-nie-nach-ca-passwort-bei/]("http://forum.ubuntuusers.de/topic/gnutls-certtool-fragt-nie-nach-ca-passwort-bei/")

As this looks quite security-relevant to me, I have filed a bug report - though no reaction on this either:

[https://bugs.launchpad.net/ubuntu/+source/gnutls26/+bug/1015919]("https://bugs.launchpad.net/ubuntu/+source/gnutls26/+bug/1015919")

---

