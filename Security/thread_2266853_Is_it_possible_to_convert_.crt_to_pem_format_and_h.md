---
title: "Is it possible to convert .crt to pem format and how?"
date: 2015-02-25
forum: Security
---

### Post by shahin on 2015-02-25
I have a .crt file, which is the certificate. I also have a private key. I understand for them to be the format used by microsoft machines. I need to load them in a nix application. Is there some way for me to get the public key from the cert, and then convert both public and private key to a format compatible with a nix machine? The destination application seems to support pem and pkcs12.

---

### Post by Habitual on 2015-02-26
You generate a private key.
Private key makes a .csr
.csr is signed by a CA and sends back a .crt
There aren't any public keys used in certificates.
Have a look at [https://www.sslshopper.com/ssl-certificate-tools.html](https://www.sslshopper.com/ssl-certificate-tools.html)

Is the *nix format destined for tomcat or apache?

---

