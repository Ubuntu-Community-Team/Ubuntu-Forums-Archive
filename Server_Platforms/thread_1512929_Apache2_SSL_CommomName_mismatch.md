---
title: "Apache2 SSL CommomName mismatch"
date: 2010-06-18
forum: Server Platforms
---

### Post by sbin on 2010-06-18
I've just migrated my website to a fresh install of Ubuntu Server 10.04 (x64), re-using my chained certificate. I am serving only one virtual host with a rewrite rule in /etc/apache2/sites-available/default to only serve https. Attempting to start Apache fails with:

[COLOR=Blue]**root@white:/var/log/apache2# tail error.log**
[Fri Jun 18 14:15:02 2010] [error] SSL Library Error: 185073780 error:0B080074x509 certificate routines:X509_check_private_key:key values mismatch
[Fri Jun 18 14:15:39 2010] [warn] RSA server certificate CommonName (CN) `menardsystems.com' does NOT match server name!?
[Fri Jun 18 14:15:39 2010] [error] Unable to configure RSA server private key
[/COLOR]

Any help will be welcomed.

Thanks, Mark

---

### Post by sjinks on 2010-06-18
It looks like the key and the certificate do not match. Just make sure you are using the correct key file.

You can try these commands to verify that the key and the cert match each other:

openssl x509 -noout -text -in /path/to/certificate.crt
  
openssl rsa -noout -text -in /path/to/key.key

You will need to check that the Modulus and the Exponent from the key matches the set from the certificate. If they don't, you will either need to find the correct key or rekey your certificate again.

---

