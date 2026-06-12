---
title: "Apache not checking crl for revoked certificates"
date: 2014-05-29
forum: Server Platforms
---

### Post by kikokimo on 2014-05-29
[COLOR=#000000][FONT=Arial]I'm having an issue I can't really identify the cause of.[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]I set-up for testing purposes a local CA and a Webserver in a VirtualBox under Ubuntu.[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]I'm willing to try Client Certificate-Authentification.[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]I got it so far, that I can't access the webserver without having a valid certificate in my browser.[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]The problem is, that after revoking the Certificate, I still access the server.[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]In my default-ssl.conf (which is loaded) I have set :[/FONT][/COLOR]
SSLCARevocationFile to /etc/ssl/CA/crl/crl.pem
[COLOR=#000000][FONT=Arial]"crl.pem" was created using "openssl ca -gencrl /etc/ssl/CA/crl/crl.pem"[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]openssl crl -in /etc/ssl/CA/crl/crl.pem -text generates the following :

[/FONT][/COLOR]
Certificate Revocation List (CRL):
        Version 2 (0x1)
    Signature Algorithm: sha256WithRSAEncryption
        Issuer: /C=AU/ST=Some-State/O=Internet Widgits Pty Ltd
        Last Update: May 29 13:10:55 2014 GMT
        Next Update: Jun 28 13:10:55 2014 GMT
        CRL extensions:
            X509v3 CRL Number: 
                4106
Revoked Certificates:
    Serial Number: 01
        Revocation Date: May 29 10:35:53 2014 GMT
    Serial Number: 02
        Revocation Date: May 29 00:32:33 2014 GMT
    Signature Algorithm: sha256WithRSAEncryption
         4a:95:31:27:df:2b:d3:5f:91:86:32:18:7e:04:1f:88:99:22:
         2b:d6:03:8d:c6:1d:81:ca:06:a0:c3:c2:cf:fe:cb:8a:ec:f9:
         7f:bb:37:4c:69:70:1e:43:0c:8e:97:89:f7:32:f8:bf:9c:3b:
         fc:b2:25:55:98:a1:fe:7f:fb:ab:79:13:67:d6:75:02:c6:74:
         03:34:bc:f3:df:61:d5:0f:e6:1e:24:8b:e7:b0:17:1b:c4:2f:
         16:56:44:8d:e4:92:1f:48:51:23:a5:1d:54:26:a4:58:6b:4d:
         07:40:bb:48:7f:c1:61:00:55:20:d2:a1:56:f9:38:fa:f9:84:
         de:2a:a5:2a:69:82:d7:8b:35:24:5b:4d:ee:c0:33:7c:b6:d6:
         83:e2:f8:79:76:f9:04:55:80:45:8c:b1:9d:5b:8d:29:65:f9:
         6d:de:d3:d2:53:6e:f0:d2:44:c9:3e:60:ca:67:0f:2b:f9:27:
         0d:36:4b:90:d5:fe:7b:23:74:6b:94:e3:93:ea:4f:90:2b:db:
         c8:96:29:4b:cc:42:f6:31:27:e6:a2:ce:a3:c8:fa:47:74:bd:
         32:51:71:f3:66:fb:2d:76:0f:ca:64:23:55:eb:f8:5e:bc:0d:
         eb:f9:e4:7a:7f:72:be:fd:1a:a7:76:32:5e:0f:21:b9:c7:2a:
         89:ac:53:26
-----BEGIN X509 CRL-----
MIIByTCBsgIBATANBgkqhkiG9w0BAQsFADBFMQswCQYDVQQGEwJBVTETMBEGA1UE
CAwKU29tZS1TdGF0ZTEhMB8GA1UECgwYSW50ZXJuZXQgV2lkZ2l0cyBQdHkgTHRk
Fw0xNDA1MjkxMzEwNTVaFw0xNDA2MjgxMzEwNTVaMCgwEgIBARcNMTQwNTI5MTAz
NTUzWjASAgECFw0xNDA1MjkwMDMyMzNaoA8wDTALBgNVHRQEBAICEAowDQYJKoZI
hvcNAQELBQADggEBAEqVMSffK9NfkYYyGH4EH4iZIivWA43GHYHKBqDDws/+y4rs
+X+7N0xpcB5DDI6Xifcy+L+cO/yyJVWYof5/+6t5E2fWdQLGdAM0vPPfYdUP5h4k
i+ewFxvELxZWRI3kkh9IUSOlHVQmpFhrTQdAu0h/wWEAVSDSoVb5OPr5hN4qpSpp
gteLNSRbTe7AM3y21oPi+Hl2+QRVgEWMsZ1bjSll+W3e09JTbvDSRMk+YMpnDyv5
Jw02S5DV/nsjdGuU45PqT5Ar28iWKUvMQvYxJ+aizqPI+kd0vTJRcfNm+y12D8pk
I1Xr+F68Dev55Hp/cr79Gqd2Ml4PIbnHKomsUyY=
-----END X509 CRL-----


[FONT=Arial]I tried both certificates with the serial 01 and 02 and I'm able to login with both of them.[/FONT]
[FONT=Arial]Does anybody has an idea what the problem may be ?[/FONT]
[FONT=Arial]Thank you ![/FONT]

---

