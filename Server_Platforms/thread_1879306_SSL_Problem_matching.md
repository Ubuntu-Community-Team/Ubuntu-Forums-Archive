---
title: "SSL Problem matching?"
date: 2011-11-11
forum: Server Platforms
---

### Post by Engineer007 on 2011-11-11
Hello All,

This might be a really easy fix, I'm not sure. I created a SSL cert for my ubuntu 10.04 server machine. I'm running a wiki off of it(it happens to be mediawiki). I created the certificate and I added it to my domain to be trusted enterprise wide. However when I go to the site now: [https://server/mediawiki/index,php/main_page](https://server/mediawiki/index,php/main_page) I get an ssl error. The error states you tried to reach server, but instead you actually reached a server identifying itself as server.domain.com. 

I tried changing the hostname and hosts files to reflect this, but I get the same error. Is this a really simple problem? I can't seem to find it through some googling. Any help would be appreciated! 


Thanks!

---

### Post by hawkmage on 2011-11-11
I am not sure how you generated you certificate but if you take a look at it using the openssl command like this:
```
openssl x509 -noout -text -in CERTFILE
```You should see something like this, it is the output from the certificate on verisign.com:
```
hawkmage@ubuntu:~$ openssl x509 -noout -text -in ~/test/Verisign_Cert.pem 
Certificate:
    Data:
        Version: 3 (0x2)
        Serial Number:
            53:d2:be:f9:24:a7:24:5e:83:ca:01:e4:6c:aa:24:77
        Signature Algorithm: sha1WithRSAEncryption
        Issuer: C=US, O=VeriSign, Inc., OU=VeriSign Trust Network, OU=Terms of use at https://www.verisign.com/rpa (c)06, CN=VeriSign Class 3 Extended Validation SSL SGC CA
        Validity
            Not Before: May 26 00:00:00 2010 GMT
            Not After : May 25 23:59:59 2012 GMT
        Subject: 1.3.6.1.4.1.311.60.2.1.3=US/1.3.6.1.4.1.311.60.2.1.2=Delaware/businessCategory=V1.0, Clause 5.(b)/serialNumber=2497886, C=US/postalCode=94043, ST=California, L=Mountain View/street=487 East Middlefield Road, O=VeriSign, Inc., OU= Production Security Services, [COLOR=Red]CN=www.verisign.com[/COLOR]
        Subject Public Key Info:
            Public Key Algorithm: rsaEncryption
                Public-Key: (2048 bit)
                Modulus:
                    00:a3:f8:fb:ef:2b:e7:d9:39:7c:27:a3:4c:93:fc:
                    e4:f2:d9:99:bd:7a:19:d9:8d:3b:4e:fd:7d:88:58:
                    11:1a:de:31:b7:d0:2e:76:b8:71:50:23:83:66:5e:
                    24:15:36:f2:47:90:16:80:8f:48:a5:56:3b:c6:77:
                    15:e6:93:2c:85:b2:e8:2d:21:63:93:67:ca:52:29:
                    d5:f5:b6:61:85:22:89:fa:2a:8f:7e:94:11:64:56:
                    4b:9d:03:5a:20:01:46:ed:4c:1f:08:71:d7:8e:96:
                    92:bb:f1:3e:12:8d:d5:4c:85:8d:7c:d7:9d:18:cd:
                    2c:3a:85:12:a5:c3:9d:b0:05:a0:f1:b4:66:44:96:
                    f3:ad:87:8d:4a:ed:35:1c:68:39:d0:57:3c:f9:48:
                    13:d6:e4:c5:21:8b:b0:16:ad:da:12:93:5e:ce:06:
                    8c:ce:ce:60:7f:8e:46:03:54:39:f0:2d:c6:d1:f3:
                    d4:8b:1c:43:a5:7b:f8:9d:49:84:83:41:49:9a:6f:
                    7c:b4:25:2f:11:c9:05:75:f8:30:7b:d2:69:c5:00:
                    b9:c3:7c:b8:8b:e3:b9:cc:41:00:86:c5:78:29:e6:
                    fa:10:d9:89:92:5e:17:af:2a:61:09:f6:fb:ed:0b:
                    a0:bb:ca:fd:96:eb:2a:26:7d:2f:f0:79:41:1c:7b:
                    da:6f
                Exponent: 65537 (0x10001)
        X509v3 extensions:
            [COLOR=Red]X509v3 Subject Alternative Name: 
                DNS:www.verisign.com, DNS:verisign.com, DNS:www.verisign.net, DNS:verisign.net, DNS:www.verisign.mobi, DNS:verisign.mobi, DNS:www.verisign.eu, DNS:verisign.eu[/COLOR]
            X509v3 Basic Constraints: 
                CA:FALSE
            X509v3 Subject Key Identifier: 
                F2:80:70:2B:F5:81:5C:26:43:5A:2D:1D:6E:E0:E0:3F:24:CA:88:92
            X509v3 Key Usage: 
                Digital Signature, Key Encipherment
            X509v3 CRL Distribution Points: 

                Full Name:
                  URI:http://EVIntl-crl.verisign.com/EVIntl2006.crl

            X509v3 Certificate Policies: 
                Policy: 2.16.840.1.113733.1.7.23.6
                  CPS: https://www.verisign.com/rpa

            X509v3 Extended Key Usage: 
                TLS Web Server Authentication, TLS Web Client Authentication, Netscape Server Gated Crypto
            X509v3 Authority Key Identifier: 
                keyid:4E:43:C8:1D:76:EF:37:53:7A:4F:F2:58:6F:94:F3:38:E2:D5:BD:DF

            Authority Information Access: 
                OCSP - URI:http://EVIntl-ocsp.verisign.com
                CA Issuers - URI:http://EVIntl-aia.verisign.com/EVIntl2006.cer

            1.3.6.1.5.5.7.1.12: 
                0`.^.\0Z0X0V..image/gif0!0.0...+......Kk.(.....R8.).K..!..0&.$http://logo.verisign.com/vslogo1.gif
    Signature Algorithm: sha1WithRSAEncryption
        7d:55:9c:41:c0:33:11:1b:28:45:59:89:18:e6:bc:14:54:6b:
        83:26:21:9e:6a:cd:b1:44:90:b4:1b:8f:ab:89:0e:c8:37:ba:
        73:d9:ad:81:86:4b:66:67:91:db:c5:72:f8:64:46:38:c8:c3:
        7a:f0:31:15:12:b8:6d:2a:2b:8b:d3:69:e0:db:b6:a5:86:59:
        e0:69:d2:90:cd:22:fc:a4:b7:66:43:ed:e3:13:09:bd:9e:f6:
        b9:0b:fe:e9:6d:ea:b2:fa:a1:85:8a:ce:08:58:d6:0e:73:81:
        ca:36:40:01:c5:79:b9:bf:4a:2e:ca:cf:07:3c:d9:13:2c:52:
        de:a7:48:0b:a9:15:d6:de:06:0d:d9:76:ca:51:63:2c:ef:3e:
        e1:26:99:18:1b:13:fc:61:04:b1:8b:9d:77:3b:67:56:54:25:
        c1:f1:2e:9e:ac:8c:fd:13:f6:dc:7d:d5:e8:08:fc:90:76:7e:
        36:cb:72:04:a0:9b:cf:bc:14:b7:4b:9e:5f:0f:8f:90:43:8d:
        c6:3e:1b:a6:4a:0f:5a:e9:2d:e1:9f:2c:3c:0d:7e:4e:89:41:
        a6:aa:04:2b:b5:27:83:46:c3:66:5a:ab:56:8b:31:10:6d:ef:
        9f:a2:d6:69:12:7f:fb:cd:84:da:b6:4d:67:8b:f9:39:8c:31:
        ff:41:eb:86
```

In this info above you will see two portions highlited in red the Subjects CN and the Subject Alternative Names.  In the certificate you will see the Subject of the certificate which should contain the Common Name or CN for the certificate.  The host in the URL you are asking should match this.  Or in the case of the VeriSigh cert above it has an options section of x509v3 attributes one of which is the Subject Alternative Name or SAN, this attribute contains alternate names that are valid for the certificate.  You can use one of the names in the SAN as the host in the URL for the site.

---

### Post by Engineer007 on 2011-11-15
Thanks for the info that did help. Instead of recreating the SSL cert I just redirected to the FQDN of the server. That resolved the "problem" seeing as it was just how I created the SSL cert. If I would have created a wildcard cert it would have worked anyways.  

-Engineer

---

