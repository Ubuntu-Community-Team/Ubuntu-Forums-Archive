---
title: "OpenSSL private key validation error [unable to load Private Key]"
date: 2014-06-20
forum: Server Platforms
---

### Post by Lucas_Rogrio_de_ on 2014-06-20
Hi Everybody,

I'm trying to validate my ssl certificate (certificate.crt) file issued by godaddy.
The following commands works very well:

```
[INDENT][I]openssl x509 -noout -modulus -in certificate.crt | openssl md5
(stdin)= bc503452072fccc6babb60b26b22ec20


openssl req -noout -modulus -in CSR.csr | openssl md5
(stdin)= bc503452072fccc6babb60b26b22ec20[/I][/INDENT]

```

The problem is on key file:

```
*openssl rsa -noout -modulus -in KEY.key | openssl md5*[INDENT]*Enter pass phrase for KEY.key:*[/INDENT]
[INDENT]*unable to load Private Key*[/INDENT]
[INDENT]*139709372356256:error:0D0680A8:asn1 encoding routines:ASN1_CHECK_TLEN:wrong tag:tasn_dec.c:1319:*[/INDENT]
[INDENT]*139709372356256:error:0D07803A:asn1 encoding routines:ASN1_ITEM_EX_D2I:nested asn1 error:tasn_dec.c:381:Type=RSA*[/INDENT]
[INDENT]*139709372356256:error:04093004:rsa routines:OLD_RSA_PRIV_DECODE:RSA lib:rsa_ameth.c:115:*[/INDENT]
[INDENT]*139709372356256:error:0D0680A8:asn1 encoding routines:ASN1_CHECK_TLEN:wrong tag:tasn_dec.c:1319:*[/INDENT]
[INDENT]*139709372356256:error:0D07803A:asn1 encoding routines:ASN1_ITEM_EX_D2I:nested asn1 error:tasn_dec.c:381:Type=PKCS8_PRIV_KEY_INFO*[/INDENT]
[INDENT]*139709372356256:error:0907B00D:PEM routines:PEM_READ_BIO_PRIVATEKEY:ASN1 lib:pem_pkey.c:132:*[/INDENT]
[INDENT][I](stdin)= d41d8cd98f00b204e9800998ecf8427e





[/I][/INDENT]

```

The KEY.key file is:

```
[INDENT]*-----BEGIN RSA PRIVATE KEY-----*[/INDENT]
[INDENT]*Proc-Type: 4,ENCRYPTED*[/INDENT]
[INDENT][I]DEK-Info: DES-EDE3-CBC,E46DFA8D69371D26

[/I][/INDENT]
[INDENT][I]private_key_content
[/I][/INDENT]
[INDENT][I]-----END RSA PRIVATE KEY-----

[/I][/INDENT]

```Somebody could help please on this matter?
Thank you very much in advance!
Regards,
Lucas.

---

