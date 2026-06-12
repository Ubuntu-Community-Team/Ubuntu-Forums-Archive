---
title: "certificates for both www and root domain"
date: 2011-03-01
forum: Server Platforms
---

### Post by mnbbrown on 2011-03-01
Hi All,

I am in the process of securing our web server (apache) using openssl generated certificates. Is it possible to generate a certificate for both [www.example.com](www.example.com) and example.com?

Thanks Matthew

---

### Post by artheus on 2011-03-01
This thread might help you.

[http://www.howtoforge.com/forums/archive/index.php/t-1585.html](http://www.howtoforge.com/forums/archive/index.php/t-1585.html)

Cheers,
Artheus

---

### Post by hawkmage on 2011-03-01
Are you looking to do a self-signed certificate or are you going to submit it to a CA to be signed?

First of all create a OpenSSL config file for the info you want if the cert:
```
[ req ]
default_bits            = 2048
default_md              = sha1
default_keyfile         = [COLOR=Red]CERT_PRIVATE_KEY.key[/COLOR]
distinguished_name      = req_distinguished_name
prompt                  = no
string_mask             = nombstr
req_extensions          = v3_req

[ req_distinguished_name ]
countryName             = [COLOR=Red]XX[/COLOR]
stateOrProvinceName     = [COLOR=Red]XX[/COLOR]
localityName            = [COLOR=Red]XX[/COLOR]
organizationName        = [COLOR=Red]XX[/COLOR]
organizationalUnitName  = [COLOR=Red]XX[/COLOR]
emailAddress            = [COLOR=Red]XX[/COLOR]
commonName              = [COLOR=Red]SITE_FQDN
[/COLOR]
[ v3_req ]
basicConstraints        = CA:FALSE
keyUsage                = nonRepudiation, digitalSignature, keyEncipherment, dataEncipherment
subjectAltName          = @alt_names

[ alt_names ]
DNS.1 = [COLOR=Red]ALT_Name1[/COLOR]
DNS.2 = [COLOR=Red]ALT_Name2[/COLOR]
```Replace the stuff in red with the your info You can add as many entries as you want under the [ alt_names ] section just continue the numbering.

For a self-signed:
```
openssl req -new -x509 -nodes -days 730 -config [COLOR=Red]YOUR_CONFIG.conf[/COLOR]  -out [COLOR=Red]YOUR_CERT.crt[/COLOR]
```Once you run this with the config file you created above you will have a [COLOR=Red]CERT_PRIVATE_KEY.key[/COLOR] and [COLOR=Red]YOUR_CERT.crt[/COLOR] which are your private key and certificate.  

For a CSR to be signed by a CA:
```
openssl req -new -nodes -days 730 -config [COLOR=Red]YOUR_CONFIG.conf[/COLOR]  -out [COLOR=Red]YOUR_REQ.csr[/COLOR]
```Once you run this with the config file you created above you will have a [COLOR=Red]CERT_PRIVATE_KEY.key[/COLOR] and [COLOR=Red]YOUR_REQ.csr[/COLOR] which are your private key and certificate signing request to submit to your CA to be signed and returned as a certificat .

---

### Post by mnbbrown on 2011-03-01
Thanks alot.

If DNS.1 = example.com & DNS.2 = [www.example.com](www.example.com) the certificate is valid for both.

Solved!!

---

### Post by hawkmage on 2011-03-01
No problem, Glad it worked for you.  I generally use the Subject Alt Names instead of a wild-card name in a certificate.  

Don't forget to mark the tread as solved.

---

