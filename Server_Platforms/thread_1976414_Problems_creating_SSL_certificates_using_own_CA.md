---
title: "Problems creating SSL certificates using own CA"
date: 2012-05-08
forum: Server Platforms
---

### Post by kennethconn on 2012-05-08
Hi,
 
I have set up my own CA to sign certificates that I create for the various services on my server (Ubuntu 11.10), using the online documentation.
I have successfully got OpenLDAP/TLS working using self-signed certificates in the past, but not using my own CA, so I do not think it is a problem with OpenLDAP configuration.
 
I was able to use my own CA to create a certificate for the server (CN=server1.example.org). So it creates the 01.pem file. This is working fine.
 
I now wish to issue another certificate for the same server for the OpenLDAP service, and I get an error of ANS1 Error in TAG (referencing --load-ca-privkey) when I use the documented certtool command.
 
I have tried using the same CN and also with a different CN (slapd1.example.org), but I get the same message.
 
I have tried using the certtool and and also openssl commands (I am not sure of exactly how I get it to read the extra options for my slapd1.info file e.g. tls_www_server, when I use the openssl command).
 
1) Has anyone any pointers as to what may be the problem here.
 
2) Also, can (or should I) use the same private key for the service that I used for the server (the --load-privkey option in certtool)?
 
Appreciate the help, has me a bit stumped. I can provide further detail if needed.
 
Thanks in advance,
Kenneth

---

### Post by hawkmage on 2012-05-08
It sounds like the OpenLDAP is not seeing your signed certificate as valid.  Have you added your CA public key to the certificate trust store for OpenLDAP?

---

### Post by kennethconn on 2012-05-08
> **hawkmage said:**
> It sounds like the OpenLDAP is not seeing your signed certificate as valid. Have you added your CA public key to the certificate trust store for OpenLDAP?
 
Hi, thanks for the reply, but I am not at that stage yet. I cannot generate a certificate in the first place. Once I get to the point where I can create the certificate, I can then work on configuring OpenLDAP correctly to use it.

---

### Post by hawkmage on 2012-05-08
OK, normally you can have a CA sign only one certificate with a subject CN atleast unless you revoke the CN.

---

### Post by kennethconn on 2012-05-08
> **hawkmage said:**
> OK, normally you can have a CA sign only one certificate with a subject CN atleast unless you revoke the CN.
 
I thought that might be an issue, but as I also tried using a different CN and still same error occurs.

---

### Post by hawkmage on 2012-05-08
Can you give more details.  What are you using for a CA?  What are the exact errors.

---

### Post by kennethconn on 2012-05-08
> **hawkmage said:**
> Can you give more details. What are you using for a CA? What are the exact errors.
 
Generating a signed certificate...
certtool: importing --load-ca-privkey: /etc/ssl/private/cakey.pem: ASN1 parser: Error in TAG.
 
Certificate is never created.

---

### Post by hawkmage on 2012-05-08
OK, what about the actual command you are using?

---

