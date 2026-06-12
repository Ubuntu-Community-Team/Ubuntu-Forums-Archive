---
title: "Installing a root CA Certificate"
date: 2016-04-05
forum: Security
---

### Post by actionmystique on 2016-04-05
Hello,

I'm trying to add Comodo's root certificates into Ubuntu 15.10 4.2.0-34.

I exported all 6 certificates from chrome 49.0.2623.110 (64-bit), imported them into XCA, exported them into .crt format.
I then unsuccessfully tried 2 different methods:


[LIST=1]
[*]**dpkg-reconfigure method**
[LIST=1]
[*]copy all crt into [COLOR=#111111][FONT=Consolas]/usr/share/ca-certificates/extra[/FONT][/COLOR]
[*][COLOR=#111111][FONT=Consolas]sudo dpkg-reconfigure ca-certificates[/FONT][/COLOR]
[*]wget -O - [https://gitlab.com/jean-christophe-manciot/PPA/raw/master/Ubuntu/dists/wily/InRelease](https://gitlab.com/jean-christophe-manciot/PPA/raw/master/Ubuntu/dists/wily/InRelease)
--2016-04-05 10:58:24--  [https://gitlab.com/jean-christophe-manciot/PPA/raw/master/Ubuntu/dists/wily/InRelease](https://gitlab.com/jean-christophe-manciot/PPA/raw/master/Ubuntu/dists/wily/InRelease)
Resolving gitlab.com (gitlab.com)... 104.210.2.228
Connecting to gitlab.com (gitlab.com)|104.210.2.228|:443... connected.
ERROR: cannot verify gitlab.com's certificate, issued by &#8216;CN=COMODO RSA Domain Validation Secure Server CA,O=COMODO CA Limited,L=Salford,ST=Greater Manchester,C=GB&#8217;:
  Unable to locally verify the issuer's authority.
[/LIST]

[*]**update-ca-certificates method**
[LIST=1]
[*]copy all crt into [COLOR=#111111][FONT=Consolas]/usr/local/share/ca-certificates/[/FONT][/COLOR]
[*][COLOR=#111111][FONT=Consolas]sudo update-ca-certificates[/FONT][/COLOR]
[*]wget -O - [https://gitlab.com/jean-christophe-manciot/PPA/raw/master/Ubuntu/dists/wily/InRelease]("https://gitlab.com/jean-christophe-manciot/PPA/raw/master/Ubuntu/dists/wily/InRelease--2016-04-05")
--2016-04-0510:58:24 --  [https://gitlab.com/jean-christophe-manciot/PPA/raw/master/Ubuntu/dists/wily/InRelease](https://gitlab.com/jean-christophe-manciot/PPA/raw/master/Ubuntu/dists/wily/InRelease)
Resolving gitlab.com (gitlab.com)... 104.210.2.228
Connecting to gitlab.com (gitlab.com)|104.210.2.228|:443... connected.
ERROR: cannot verify gitlab.com's certificate, issued by &#8216;CN=COMODO RSA Domain Validation Secure Server CA,O=COMODO CA Limited,L=Salford,ST=Greater Manchester,C=GB&#8217;:
  Unable to locally verify the issuer's authority.

A few additional comments:
- I'm a little surprised that on my system, there is no [COLOR=#111111][FONT=Consolas]/etc/ca-certificates.conf
[/FONT][/COLOR]- my account on gitlab has a 2-factor authentication: removing it does not solve that issue.
- I also tried to download a file from Comodo's server:
wget -O - [https://support.comodo.com/index.php?/Default/Knowledgebase/Article/View/969](https://support.comodo.com/index.php?/Default/Knowledgebase/Article/View/969) 
--2016-04-05 11:17:06--  [https://support.comodo.com/index.php?/Default/Knowledgebase/Article/View/969](https://support.comodo.com/index.php?/Default/Knowledgebase/Article/View/969)
Resolving support.comodo.com (support.comodo.com)... 91.199.212.147
Connecting to support.comodo.com (support.comodo.com)|91.199.212.147|:443... connected.
ERROR: cannot verify support.comodo.com's certificate, issued by &#8216;CN=COMODO RSA Extended Validation Secure Server CA,O=COMODO CA Limited,L=Salford,ST=Greater Manchester,C=GB&#8217;:
  Self-signed certificate encountered.

Any suggestion?
[/LIST]
[/LIST]

---

### Post by actionmystique on 2016-04-05
I tried to add the exact ca certificate specified in the error message directly from Comodo: [Comodo RSA Domain Validation Secure Server CA]("https://support.comodo.com/index.php?/Knowledgebase/Article/View/970/0/intermediate-2-sha-2-comodo-rsa-domain-validation-secure-server-ca")
No success with the same error message as first post.

Maybe the issue comes from the lack of [COLOR=#111111][FONT=Consolas]/etc/ca-certificates.conf
[/FONT][/COLOR]But reinstalling ca-certificates package does not install it.

---

### Post by actionmystique on 2016-04-05
I've installed all the following extra Comodo's certificates from Chrome, Firefox and Comodo:
[LIST]
[*]AAA_Certificate_Services.crt
[*]COMODO_ECC_Domain_Validation_Secure_Server_CA_2.crt
[*]COMODO_RSA_Organization_Validation_Secure_Server_CA.crt
[*]COMODO_Certification_Authority.crt
[*]COMODO_RSA_Certification_Authority.crt
[*]Secure_Certificate_Service.crt
[*]COMODO_ECC_Certification_Authority.crt
[*]comodorsadomainvalidationsecureserverca.crt
[*]Trusted_Certificate_Services.crt
[/LIST]
Still the same error message.
No more clues.

---

### Post by actionmystique on 2016-04-05
Reinstalling openssl solved this issue.
BTW, I removed all unnecessary Comodo's certificates and kept only the following:
[LIST]
[*]**[Comodo RSA Certification Authority]("https://support.comodo.com/index.php?/Default/Knowledgebase/Article/View/969") **(available by default)
[*][**Comodo RSA Domain Validation Secure Server CA**]("https://support.comodo.com/index.php?/Knowledgebase/Article/View/970/0/intermediate-2-sha-2-comodo-rsa-domain-validation-secure-server-ca")
[/LIST]
Then, I've been able to use it for gitlab:

```
wget -O - [https://gitlab.com/jean-christophe-manciot/PPA/raw/master/Ubuntu/dists/wily/InRelease](https://gitlab.com/jean-christophe-manciot/PPA/raw/master/Ubuntu/dists/wily/InRelease)
--2016-04-05 16:10:36--  [https://gitlab.com/jean-christophe-manciot/PPA/raw/master/Ubuntu/dists/wily/InRelease](https://gitlab.com/jean-christophe-manciot/PPA/raw/master/Ubuntu/dists/wily/InRelease)
Resolving gitlab.com (gitlab.com)... 104.210.2.228
Connecting to gitlab.com (gitlab.com)|104.210.2.228|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 2993 (2,9K) [text/plain]
Saving to: &#8216;STDOUT&#8217;
-                                       0%[                                                                          ]       0  --.-KB/s             -----BEGIN PGP SIGNED MESSAGE-----
Hash: SHA256
...
-                                     100%[=========================================================================>]   2,92K  --.-KB/s   in 0s     


2016-04-05 16:10:36 (902 MB/s) - written to stdout [2993/2993]
```

---

