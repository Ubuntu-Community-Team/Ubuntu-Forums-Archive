---
title: "stuck on implementing PKI"
date: 2010-07-26
forum: Security
---

### Post by warda on 2010-07-26
hi I was playing around with securing server.
 
I followed instruction from here: [https://help.ubuntu.com/community/OpenSSL](https://help.ubuntu.com/community/OpenSSL) 
 
when i got to the point 
**openssl ca -in tempreq.pem -out server_crt.pem**
[FONT=Verdana]to sign the certificate Im getting following error:[/FONT]

[FONT=Verdana]Using[/FONT] configuration from /home/admin/myCA/caconfig.cnf
error on line 1 of config file '/home/admin/myCA/caconfig.cnf'
1283:error:0E079065:configuration file routines:DEF_LOAD_BIO:missing equal sign:conf_def.c:366:line 1
 
[FONT=Verdana]I guess I might need to change something with **caconfig.cnf** file but don't know what...[/FONT]

[FONT=Verdana]was trying to google error but nothing i could work on comes..[/FONT]

[FONT=Verdana]could any1 with idea of what is wrong help me please?[/FONT]

[FONT=Verdana]thank you[/FONT]

---

### Post by warda on 2010-07-26
> **warda said:**
> 1283:error:0E079065:configuration file routines:D
 
 
the smile after routines is meant to be : D but without space beetwen. thanks

---

### Post by cdenley on 2010-07-26
> **warda said:**
> the smile after routines is meant to be : D but without space beetwen. thanks

You should enclose output like that in "CODE" tags.
[NOPARSE]
```

code goes here
:D

```
[/NOPARSE]
which results in:
```

code goes here
:D

```

---

### Post by warda on 2010-07-26
> **cdenley said:**
> You should enclose output like that in "CODE" tags.
[NOPARSE]
```

code goes here
:D

```
[/NOPARSE]
which results in:
```

code goes here
:D

```
 
 
I see, thanks for that.. 
 
do you have some thoughts as of the issue? 
 
have you happend to have similiar problem? it is still the same testing server ;) so no pressure though would like to know how to sort it out. 
I'm considering myself whether I should not just run all the steps again.. but maybe just some component of openssl is broken and needs to be reinstalled?
 
thanks
 
if any one feels needs more info please let me know as Im not sure what else to add.. basically done all the steps as per link frm 1st post

---

### Post by Bachstelze on 2010-07-26
Apparently there's an error in your caconfig.cnf, so we need to see it.

---

### Post by warda on 2010-07-26
hi I decided run everything once again.
 
now I try to sign certificat I get when I run 
**openssl ca -in tempreq.pem -out server_crt.pem**
Iam being asked for passphrase which I supply press enter and get 
```
 
**CA certificate and CA private key do not match**
**1430:error:0B080074:x509 certificate routines:X509_check_private_key:key values mismatch:x509_cmp.c:406:**
**unable to write 'random state'**
```
 
what a mess :/
 
anyhow my question are:
1.are all the steps from [https://help.ubuntu.com/community/OpenSSL](https://help.ubuntu.com/community/OpenSSL) meant to be run on single machine?
2.maybe I just need to start a fresh, how would I get rid of all my certs issued so far? including the very first one issued for CA?
 
thanks

---

### Post by Bachstelze on 2010-07-26
> **warda said:**
> 
1.are all the steps from [https://help.ubuntu.com/community/OpenSSL](https://help.ubuntu.com/community/OpenSSL) meant to be run on single machine?


Yes.  What are you trying to do, though?  If you just want to use SSL in Apache or something similar, you should already have an SSL certificate that was created when you installed it.

---

### Post by warda on 2010-07-26
hi and thanks for follow up,
 
yes I am trying to get apache to use ssl. 
basically I secured part of the website with htpaswd, htaccess and now want to get credentials to be encrypted when supplied for access. 
 
I didn't know that i install ssl certificate while installing apache... well i'm quiet new to all of that...
 
so if I install apache do I authomatically turn ubuntu box in the CA too? I can't remember that I was required to give any pass phrase while installing apache though...

---

### Post by Bachstelze on 2010-07-26
> **warda said:**
> 
I didn't know that i install ssl certificate while installing apache... well i'm quiet new to all of that...
 
so if I install apache do I authomatically turn ubuntu box in the CA too? I can't remember that I was required to give any pass phrase while installing apache though...

As per /etc/apache2/sites-available/ssl-default, the SSL certificate created at installation is at

```
        SSLCertificateFile    /etc/ssl/certs/ssl-cert-snakeoil.pem
        SSLCertificateKeyFile /etc/ssl/private/ssl-cert-snakeoil.key

```

There is no CA created.  Depending on what you want, it might or might not be enough for you, but if you want to create your own CA and certificates, you will have to do some reading so you know what you're doing (blindly copy-and-paste'ing commands from a Wiki is very error prone).

---

