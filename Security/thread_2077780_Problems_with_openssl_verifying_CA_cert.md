---
title: "Problems with openssl verifying CA cert"
date: 2012-10-29
forum: Security
---

### Post by mrlizard123 on 2012-10-29
I am hoping someone can help me out with this.

I have a server (Ubuntu 12.04.1 LTS) with pretty much the exact same problem as described here by someone else:
[http://serverfault.com/questions/373920/ubuntu-11-10-using-wget-curl-fails-with-ssl](http://serverfault.com/questions/373920/ubuntu-11-10-using-wget-curl-fails-with-ssl)

In summary:
```
wget https://test.sagepay.com
```
gives
```
--2012-10-29 14:37:59--  https://test.sagepay.com/
Resolving test.sagepay.com (test.sagepay.com)... 195.170.169.8
Connecting to test.sagepay.com (test.sagepay.com)|195.170.169.8|:443... connected.
ERROR: cannot verify test.sagepay.com's certificate, issued by `/C=US/O=VeriSign, Inc./OU=VeriSign Trust Network/OU=Terms of use at https://www.verisign.com/rpa
 (c)06/CN=VeriSign Class 3 Extended Validation SSL SGC CA':
  Unable to locally verify the issuer's authority.
To connect to test.sagepay.com insecurely, use `--no-check-certificate'.
```

and
```
curl -Iv https://test.sagepay.com
```
gives
```
* About to connect() to test.sagepay.com port 443 (#0)
*   Trying 195.170.169.8... connected
* successfully set certificate verify locations:
*   CAfile: none
  CApath: /etc/ssl/certs
* SSLv3, TLS handshake, Client hello (1):
* SSLv3, TLS handshake, Server hello (2):
* SSLv3, TLS handshake, CERT (11):
* SSLv3, TLS alert, Server hello (2):
* SSL certificate problem, verify that the CA cert is OK. Details:
error:14090086:SSL routines:SSL3_GET_SERVER_CERTIFICATE:certificate verify failed
* Closing connection #0
curl: (60) SSL certificate problem, verify that the CA cert is OK. Details:
error:14090086:SSL routines:SSL3_GET_SERVER_CERTIFICATE:certificate verify failed
More details here: http://curl.haxx.se/docs/sslcerts.html

curl performs SSL certificate verification by default, using a "bundle"
 of Certificate Authority (CA) public keys (CA certs). If the default
 bundle file isn't adequate, you can specify an alternate file
 using the --cacert option.
If this HTTPS server uses a certificate signed by a CA represented in
 the bundle, the certificate verification probably failed due to a
 problem with the certificate (it might be expired, or the name might
 not match the domain name in the URL).
If you'd like to turn off curl's verification of the certificate, use
 the -k (or --insecure) option.
```

So the problem appears to be the same, even down to the site.

using the link name found by user "cjc" I get the same:
```
$ ls -la 7651b327.0
lrwxrwxrwx 1 root root 59 Oct 29 13:34 7651b327.0 -> Verisign_Class_3_Public_Primary_Certification_Authority.pem
$ ls -la Verisign_Class_3_Public_Primary_Certification_Authority.pem
lrwxrwxrwx 1 root root 94 Sep  6 15:46 Verisign_Class_3_Public_Primary_Certification_Authority.pem -> /usr/share/ca-certificates/mozilla/Verisign_Class_3_Public
_Primary_Certification_Authority.crt
$ ls -la /usr/share/ca-certificates/mozilla/Verisign_Class_3_Public_Primary_Certification_Authority.crt
-rw-r--r-- 1 root root 834 Feb  7  2012 /usr/share/ca-certificates/mozilla/Verisign_Class_3_Public_Primary_Certification_Authority.crt
$ more /usr/share/ca-certificates/mozilla/Verisign_Class_3_Public_Primary_Certification_Authority.crt
-----BEGIN CERTIFICATE-----
MIICPDCCAaUCEDyRMcsf9tAbDpq40ES/Er4wDQYJKoZIhvcNAQEFBQAwXzELMAkG
A1UEBhMCVVMxFzAVBgNVBAoTDlZlcmlTaWduLCBJbmMuMTcwNQYDVQQLEy5DbGFz
cyAzIFB1YmxpYyBQcmltYXJ5IENlcnRpZmljYXRpb24gQXV0aG9yaXR5MB4XDTk2
MDEyOTAwMDAwMFoXDTI4MDgwMjIzNTk1OVowXzELMAkGA1UEBhMCVVMxFzAVBgNV
BAoTDlZlcmlTaWduLCBJbmMuMTcwNQYDVQQLEy5DbGFzcyAzIFB1YmxpYyBQcmlt
YXJ5IENlcnRpZmljYXRpb24gQXV0aG9yaXR5MIGfMA0GCSqGSIb3DQEBAQUAA4GN
ADCBiQKBgQDJXFme8huKARS0EN8EQNvjV69qRUCPhAwL0TPZ2RHP7gJYHyX3KqhE
BarsAx94f56TuZoAqiN91qyFomNFx3InzPRMxnVx0jnvT0Lwdd8KkMaOIG+YD/is
I19wKTakyYbnsZogy1Olhec9vn2a/iRFM9x2Fe0PonFkTGUugWhFpwIDAQABMA0G
CSqGSIb3DQEBBQUAA4GBABByUqkFFBkyCEHwxWsKzH4PIRnN5GfcX6kb5sroc50i
2JhucwNhkcV8sEVAbkSdjbCxlnRhLQ2pRdKkkirWmnWXbj9T/UWZYB2oK0z5XqcJ
2HUw19JlYD1n1khVdWk/kfVIC0dpImmClr7JyDiGSnoscxlIaU5rfGW/D/xwzoiQ
-----END CERTIFICATE-----
$

```

running the strace myself
```
strace -o /tmp/foo.out curl -Iv https://test.sagepay.com
```

and grep for ssl
```
open("/lib/i386-linux-gnu/libssl.so.1.0.0", O_RDONLY|O_CLOEXEC) = 3
stat64("/etc/ssl/certs/415660c1.0", {st_mode=S_IFREG|0644, st_size=834, ...}) = 0
open("/etc/ssl/certs/415660c1.0", O_RDONLY|O_LARGEFILE) = 4
stat64("/etc/ssl/certs/415660c1.1", 0xbffcc210) = -1 ENOENT (No such file or directory)
```

then looking at the link
```
$ ls -la 415660c1.0
lrwxrwxrwx 1 root root 59 Oct 29 13:34 415660c1.0 -> Verisign_Class_3_Public_Primary_Certification_Authority.pem
```

it's the same as the previous link.

So I can follow the whole post for the question and the edits and have the same issue; when it gets to the "Answered below" and I read the answer I'm not happy about the idea of just copying a certificate from a website and installing it.

I looked on verisign's website and the listed certificate for "Class 3 Public Primary Certification Authority" is not the same as the one given in that answer (or at [http://curl.haxx.se/ca/cacert.pem](http://curl.haxx.se/ca/cacert.pem)) so I'm wary of just installing it.

Any advice on how I can resolve this without just installing that certificate? (or perhaps explaining why I *should* just install that certificate?)

Thanks in advance

---

