---
title: "Apache SSL do not work in expected way"
date: 2011-06-12
forum: Server Platforms
---

### Post by Abadon_ on 2011-06-12
Hello,

Yesterday my site's Rapid SSL certificate expire for that reason I bought new one - Thawte 123 certificate. I installed new SSL with this lines in vhost configuration for my site:

>  SSLEngine on
        SSLCertificateFile    /etc/ssl/certs/support.nextpointhost.com.crt
        SSLCertificateKeyFile /etc/ssl/private/support.nextpointhost.com.key
        SSLCACertificatePath /etc/ssl/certs/
        SSLCACertificateFile /etc/ssl/certs/SSL123_CA_Bundle.pem

In client's browsers everything is fine, but in apache error log I see many lines like this:

> [Fri Jun 10 10:34:29 2011] [notice] caught SIGTERM, shutting down
[Fri Jun 10 10:34:33 2011] [warn] Init: Name-based SSL virtual hosts only work for clients with TLS server name indication support (RFC 4366)
[Fri Jun 10 10:34:34 2011] [warn] Init: Name-based SSL virtual hosts only work for clients with TLS server name indication support (RFC 4366)
[Fri Jun 10 10:34:34 2011] [notice] Apache/2.2.14 (Ubuntu) PHP/5.2.10-2ubuntu6.7 with Suhosin-Patch mod_ssl/2.2.14 OpenSSL/0.9.8k configured -- resuming normal operations

Also when I go to Thawte SSL check I see errors that certificate is not correctly installed and **openssl s_client -host 213.145.124.4 -port 443 -showcerts** show errors too:

> CONNECTED(00000003)
depth=0 /O=support.nextpointhost.com/OU=Go to [https://www.thawte.com/repository/index.html/OU=Thawte](https://www.thawte.com/repository/index.html/OU=Thawte) SSL123 certificate/OU=Domain Validated/CN=support.nextpointhost.com
verify error:num=20:unable to get local issuer certificate
verify return:1
depth=0 /O=support.nextpointhost.com/OU=Go to [https://www.thawte.com/repository/index.html/OU=Thawte](https://www.thawte.com/repository/index.html/OU=Thawte) SSL123 certificate/OU=Domain Validated/CN=support.nextpointhost.com
verify error:num=27:certificate not trusted
verify return:1
depth=0 /O=support.nextpointhost.com/OU=Go to [https://www.thawte.com/repository/index.html/OU=Thawte](https://www.thawte.com/repository/index.html/OU=Thawte) SSL123 certificate/OU=Domain Validated/CN=support.nextpointhost.com
[B]verify error:num=21:unable to verify the first certificate
verify return:1[/B]
---
Certificate chain
 0 s:/O=support.nextpointhost.com/OU=Go to [https://www.thawte.com/repository/index.html/OU=Thawte](https://www.thawte.com/repository/index.html/OU=Thawte) SSL123 certificate/OU=Domain Validated/CN=support.nextpointhost.com
   i:/C=US/O=Thawte, Inc./OU=Domain Validated SSL/CN=Thawte DV SSL CA
-----BEGIN CERTIFICATE-----
MIIETjCCAzagAwIBAgIQWIYknSaZZRr6R6TvHNqEtzANBgkqhkiG9w0BAQUFADBe
MQswCQYDVQQGEwJVUzEVMBMGA1UEChMMVGhhd3RlLCBJbmMuMR0wGwYDVQQLExRE
b21haW4gVmFsaWRhdGVkIFNTTDEZMBcGA1UEAxMQVGhhd3RlIERWIFNTTCBDQTAe
Fw0xMTA2MDkwMDAwMDBaFw0xMjA3MDgyMzU5NTlaMIHEMSIwIAYDVQQKFBlzdXBw
b3J0Lm5leHRwb2ludGhvc3QuY29tMTswOQYDVQQLEzJHbyB0byBodHRwczovL3d3
dy50aGF3dGUuY29tL3JlcG9zaXRvcnkvaW5kZXguaHRtbDEiMCAGA1UECxMZVGhh
d3RlIFNTTDEyMyBjZXJ0aWZpY2F0ZTEZMBcGA1UECxMQRG9tYWluIFZhbGlkYXRl
ZDEiMCAGA1UEAxQZc3VwcG9ydC5uZXh0cG9pbnRob3N0LmNvbTCCASIwDQYJKoZI
hvcNAQEBBQADggEPADCCAQoCggEBANfa8CSAB8CU50fbLt+BPZcZJushhML+JBM4
AxjYkSONutdw18AZXkiKkMVLCeyKXuSJtxX1VxF4Wnb0fT6YF96yRlUm8MD0TLCI
9AkpLAyvjlM4lAw6mSjCCGOp/ZTo+HhGn0WHYpRjJc05GViLraTN6fMD/fxuI8fU
XsyJopDFVEDJHV2i1jH7Jjh6Z7bPphc0qgZp1+BPFpKF8o0NkfVvUJgbxPkzK1CZ
Pvu3ZanqBac46ScGc+sp+ZdjpvJQ++xv+E8BckGiKeaGbDYOl5DfGoy6iBVDHif9
zXEKYUBEnp8zn1zc2ef5I/jdeRjcOe4GpUloLg+oRE+rrHnU2S8CAwEAAaOBoDCB
nTAMBgNVHRMBAf8EAjAAMDoGA1UdHwQzMDEwL6AtoCuGKWh0dHA6Ly9zdnItZHYt
Y3JsLnRoYXd0ZS5jb20vVGhhd3RlRFYuY3JsMB0GA1UdJQQWMBQGCCsGAQUFBwMB
BggrBgEFBQcDAjAyBggrBgEFBQcBAQQmMCQwIgYIKwYBBQUHMAGGFmh0dHA6Ly9v
Y3NwLnRoYXd0ZS5jb20wDQYJKoZIhvcNAQEFBQADggEBAMdfffm4cboBcR75qyVN
rIJOYJ3JhcJMQbOXR1x0ejuV0YR2oPmauu5ac1pLmnKMBu3JC0/Fe4fis/Hf6FFb
WngaANsXuq3booJyRMsxtMtETIrH2rN6Da/P7UlspgvRjytYdzbVAvCr91oB5xb2
OEz9Dt1D+ZObey89IrS5rUuJwH9R/31MCpEKz7l3cuMHPoK0F3kO7U0ffjkEfc17
9S9v2UC+qbxI7rY8CqlS7vtUfHegN3/Ajf7PzUuXSx8QjdBvL0lyLRUg+tqypU54
0xvnn9ictLgO948A07ro3OhuzkXhy3SWliUaTnyQe9nBsX3d2uJ+CNN6KRaJmTtg
AcM=
-----END CERTIFICATE-----
---
Server certificate
subject=/O=support.nextpointhost.com/OU=Go to [https://www.thawte.com/repository/index.html/OU=Thawte](https://www.thawte.com/repository/index.html/OU=Thawte) SSL123 certificate/OU=Domain Validated/CN=support.nextpointhost.com
issuer=/C=US/O=Thawte, Inc./OU=Domain Validated SSL/CN=Thawte DV SSL CA
---
**No client certificate CA names sent**
---
SSL handshake has read 1798 bytes and written 316 bytes
---
New, TLSv1/SSLv3, Cipher is DHE-RSA-AES256-SHA
Server public key is 2048 bit
Compression: NONE
Expansion: NONE
SSL-Session:
    Protocol  : TLSv1
    Cipher    : DHE-RSA-AES256-SHA
    Session-ID: FEF23FA5B76319FF75735325A11CF4E226A469C0366EB0D6E9FB3C3525EF5CAD
    Session-ID-ctx: 
    Master-Key: A5A987C3D34FCD71ACE5A389C496C54636521943268044C311FDA63004CEC4D57D2A3F1DA3D2FF9F55B3BD1BC0BC405B
    Key-Arg   : None
    Start Time: 1307785095
    Timeout   : 300 (sec)
**    Verify return code: 21 (unable to verify the first certificate)**
---

closed

When I run this test and manually specify path to certification authority everything is fine bellow you can see results of  **openssl s_client -CApath /etc/ssl/certs/ -connect support.nextpointhost.com:443**

> CONNECTED(00000003)
depth=3 /C=ZA/ST=Western Cape/L=Cape Town/O=Thawte Consulting cc/OU=Certification Services Division/CN=Thawte Premium Server CA/emailAddress=premium-server@thawte.com
verify return:1
depth=2 /C=US/O=thawte, Inc./OU=Certification Services Division/OU=(c) 2006 thawte, Inc. - For authorized use only/CN=thawte Primary Root CA
verify return:1
depth=1 /C=US/O=Thawte, Inc./OU=Domain Validated SSL/CN=Thawte DV SSL CA
verify return:1
depth=0 /O=support.nextpointhost.com/OU=Go to [https://www.thawte.com/repository/index.html/OU=Thawte](https://www.thawte.com/repository/index.html/OU=Thawte) SSL123 certificate/OU=Domain Validated/CN=support.nextpointhost.com
**verify return:1**
---
Certificate chain
 0 s:/O=support.nextpointhost.com/OU=Go to [https://www.thawte.com/repository/index.html/OU=Thawte](https://www.thawte.com/repository/index.html/OU=Thawte) SSL123 certificate/OU=Domain Validated/CN=support.nextpointhost.com
   i:/C=US/O=Thawte, Inc./OU=Domain Validated SSL/CN=Thawte DV SSL CA
---
Server certificate
-----BEGIN CERTIFICATE-----
MIIETjCCAzagAwIBAgIQWIYknSaZZRr6R6TvHNqEtzANBgkqhkiG9w0BAQUFADBe
MQswCQYDVQQGEwJVUzEVMBMGA1UEChMMVGhhd3RlLCBJbmMuMR0wGwYDVQQLExRE
b21haW4gVmFsaWRhdGVkIFNTTDEZMBcGA1UEAxMQVGhhd3RlIERWIFNTTCBDQTAe
Fw0xMTA2MDkwMDAwMDBaFw0xMjA3MDgyMzU5NTlaMIHEMSIwIAYDVQQKFBlzdXBw
b3J0Lm5leHRwb2ludGhvc3QuY29tMTswOQYDVQQLEzJHbyB0byBodHRwczovL3d3
dy50aGF3dGUuY29tL3JlcG9zaXRvcnkvaW5kZXguaHRtbDEiMCAGA1UECxMZVGhh
d3RlIFNTTDEyMyBjZXJ0aWZpY2F0ZTEZMBcGA1UECxMQRG9tYWluIFZhbGlkYXRl
ZDEiMCAGA1UEAxQZc3VwcG9ydC5uZXh0cG9pbnRob3N0LmNvbTCCASIwDQYJKoZI
hvcNAQEBBQADggEPADCCAQoCggEBANfa8CSAB8CU50fbLt+BPZcZJushhML+JBM4
AxjYkSONutdw18AZXkiKkMVLCeyKXuSJtxX1VxF4Wnb0fT6YF96yRlUm8MD0TLCI
9AkpLAyvjlM4lAw6mSjCCGOp/ZTo+HhGn0WHYpRjJc05GViLraTN6fMD/fxuI8fU
XsyJopDFVEDJHV2i1jH7Jjh6Z7bPphc0qgZp1+BPFpKF8o0NkfVvUJgbxPkzK1CZ
Pvu3ZanqBac46ScGc+sp+ZdjpvJQ++xv+E8BckGiKeaGbDYOl5DfGoy6iBVDHif9
zXEKYUBEnp8zn1zc2ef5I/jdeRjcOe4GpUloLg+oRE+rrHnU2S8CAwEAAaOBoDCB
nTAMBgNVHRMBAf8EAjAAMDoGA1UdHwQzMDEwL6AtoCuGKWh0dHA6Ly9zdnItZHYt
Y3JsLnRoYXd0ZS5jb20vVGhhd3RlRFYuY3JsMB0GA1UdJQQWMBQGCCsGAQUFBwMB
BggrBgEFBQcDAjAyBggrBgEFBQcBAQQmMCQwIgYIKwYBBQUHMAGGFmh0dHA6Ly9v
Y3NwLnRoYXd0ZS5jb20wDQYJKoZIhvcNAQEFBQADggEBAMdfffm4cboBcR75qyVN
rIJOYJ3JhcJMQbOXR1x0ejuV0YR2oPmauu5ac1pLmnKMBu3JC0/Fe4fis/Hf6FFb
WngaANsXuq3booJyRMsxtMtETIrH2rN6Da/P7UlspgvRjytYdzbVAvCr91oB5xb2
OEz9Dt1D+ZObey89IrS5rUuJwH9R/31MCpEKz7l3cuMHPoK0F3kO7U0ffjkEfc17
9S9v2UC+qbxI7rY8CqlS7vtUfHegN3/Ajf7PzUuXSx8QjdBvL0lyLRUg+tqypU54
0xvnn9ictLgO948A07ro3OhuzkXhy3SWliUaTnyQe9nBsX3d2uJ+CNN6KRaJmTtg
AcM=
-----END CERTIFICATE-----
subject=/O=support.nextpointhost.com/OU=Go to [https://www.thawte.com/repository/index.html/OU=Thawte](https://www.thawte.com/repository/index.html/OU=Thawte) SSL123 certificate/OU=Domain Validated/CN=support.nextpointhost.com
issuer=/C=US/O=Thawte, Inc./OU=Domain Validated SSL/CN=Thawte DV SSL CA
---
No client certificate CA names sent
---
SSL handshake has read 1798 bytes and written 316 bytes
---
New, TLSv1/SSLv3, Cipher is DHE-RSA-AES256-SHA
Server public key is 2048 bit
Compression: NONE
Expansion: NONE
SSL-Session:
    Protocol  : TLSv1
    Cipher    : DHE-RSA-AES256-SHA
    Session-ID: B3B1119B5E771BABD31E060F9326CF86341644637F4815F9CB14E46E693D72A5
    Session-ID-ctx: 
    Master-Key: 1591812D02364F458DC7EDC58E8ADB27B4DC0D5B6EAED53333C7DFFD5430DD4542290CAA854A8C2E4A04138E21F35E62
    Key-Arg   : None
    Start Time: 1307785427
    Timeout   : 300 (sec)
   ** Verify return code: 0 (ok)**
---

closed

My question is why Apache do not want to read CAbundle file maybe I was configure something wrong?

Thank you in advance of all guys who will help me and I sorry for my bad English.

---

### Post by hawkmage on 2011-06-13
In the first openssl command using s_client you are using the IP address of the web site.  This doesn't match the CN of the subject of your sites certificate.  This is why the verification fails.

As for the CA Bundle is being sent out properly, why do you think is is not working?

---

### Post by BkkBonanza on 2011-06-13
Your domain seems to work fine for me testing using FF here.

---

### Post by Abadon_ on 2011-06-16
Hello,

In browser I see that working but why apache show this errors. I repeat test with openssl s_client -host support.nextpointhost.com -port 443 -showcerts
> CONNECTED(00000003)
depth=3 /C=ZA/ST=Western Cape/L=Cape Town/O=Thawte Consulting cc/OU=Certification Services Division/CN=Thawte Premium Server CA/emailAddress=premium-server@thawte.com
verify error:num=19:self signed certificate in certificate chain
verify return:0
---
Certificate chain
 0 s:/O=support.nextpointhost.com/OU=Go to [https://www.thawte.com/repository/index.html/OU=Thawte](https://www.thawte.com/repository/index.html/OU=Thawte) SSL123 certificate/OU=Domain Validated/CN=support.nextpointhost.com
   i:/C=US/O=Thawte, Inc./OU=Domain Validated SSL/CN=Thawte DV SSL CA
-----BEGIN CERTIFICATE-----
MIIETjCCAzagAwIBAgIQWIYknSaZZRr6R6TvHNqEtzANBgkqhkiG9w0BAQUFADBe
MQswCQYDVQQGEwJVUzEVMBMGA1UEChMMVGhhd3RlLCBJbmMuMR0wGwYDVQQLExRE
b21haW4gVmFsaWRhdGVkIFNTTDEZMBcGA1UEAxMQVGhhd3RlIERWIFNTTCBDQTAe
Fw0xMTA2MDkwMDAwMDBaFw0xMjA3MDgyMzU5NTlaMIHEMSIwIAYDVQQKFBlzdXBw
b3J0Lm5leHRwb2ludGhvc3QuY29tMTswOQYDVQQLEzJHbyB0byBodHRwczovL3d3
dy50aGF3dGUuY29tL3JlcG9zaXRvcnkvaW5kZXguaHRtbDEiMCAGA1UECxMZVGhh
d3RlIFNTTDEyMyBjZXJ0aWZpY2F0ZTEZMBcGA1UECxMQRG9tYWluIFZhbGlkYXRl
ZDEiMCAGA1UEAxQZc3VwcG9ydC5uZXh0cG9pbnRob3N0LmNvbTCCASIwDQYJKoZI
hvcNAQEBBQADggEPADCCAQoCggEBANfa8CSAB8CU50fbLt+BPZcZJushhML+JBM4
AxjYkSONutdw18AZXkiKkMVLCeyKXuSJtxX1VxF4Wnb0fT6YF96yRlUm8MD0TLCI
9AkpLAyvjlM4lAw6mSjCCGOp/ZTo+HhGn0WHYpRjJc05GViLraTN6fMD/fxuI8fU
XsyJopDFVEDJHV2i1jH7Jjh6Z7bPphc0qgZp1+BPFpKF8o0NkfVvUJgbxPkzK1CZ
Pvu3ZanqBac46ScGc+sp+ZdjpvJQ++xv+E8BckGiKeaGbDYOl5DfGoy6iBVDHif9
zXEKYUBEnp8zn1zc2ef5I/jdeRjcOe4GpUloLg+oRE+rrHnU2S8CAwEAAaOBoDCB
nTAMBgNVHRMBAf8EAjAAMDoGA1UdHwQzMDEwL6AtoCuGKWh0dHA6Ly9zdnItZHYt
Y3JsLnRoYXd0ZS5jb20vVGhhd3RlRFYuY3JsMB0GA1UdJQQWMBQGCCsGAQUFBwMB
BggrBgEFBQcDAjAyBggrBgEFBQcBAQQmMCQwIgYIKwYBBQUHMAGGFmh0dHA6Ly9v
Y3NwLnRoYXd0ZS5jb20wDQYJKoZIhvcNAQEFBQADggEBAMdfffm4cboBcR75qyVN
rIJOYJ3JhcJMQbOXR1x0ejuV0YR2oPmauu5ac1pLmnKMBu3JC0/Fe4fis/Hf6FFb
WngaANsXuq3booJyRMsxtMtETIrH2rN6Da/P7UlspgvRjytYdzbVAvCr91oB5xb2
OEz9Dt1D+ZObey89IrS5rUuJwH9R/31MCpEKz7l3cuMHPoK0F3kO7U0ffjkEfc17
9S9v2UC+qbxI7rY8CqlS7vtUfHegN3/Ajf7PzUuXSx8QjdBvL0lyLRUg+tqypU54
0xvnn9ictLgO948A07ro3OhuzkXhy3SWliUaTnyQe9nBsX3d2uJ+CNN6KRaJmTtg
AcM=
-----END CERTIFICATE-----
 1 s:/C=US/O=Thawte, Inc./OU=Domain Validated SSL/CN=Thawte DV SSL CA
   i:/C=US/O=thawte, Inc./OU=Certification Services Division/OU=(c) 2006 thawte, Inc. - For authorized use only/CN=thawte Primary Root CA
-----BEGIN CERTIFICATE-----
MIIEjzCCA3egAwIBAgIQdhASihe2grs6H50amjXAkjANBgkqhkiG9w0BAQUFADCB
qTELMAkGA1UEBhMCVVMxFTATBgNVBAoTDHRoYXd0ZSwgSW5jLjEoMCYGA1UECxMf
Q2VydGlmaWNhdGlvbiBTZXJ2aWNlcyBEaXZpc2lvbjE4MDYGA1UECxMvKGMpIDIw
MDYgdGhhd3RlLCBJbmMuIC0gRm9yIGF1dGhvcml6ZWQgdXNlIG9ubHkxHzAdBgNV
BAMTFnRoYXd0ZSBQcmltYXJ5IFJvb3QgQ0EwHhcNMTAwMjE4MDAwMDAwWhcNMjAw
MjE3MjM1OTU5WjBeMQswCQYDVQQGEwJVUzEVMBMGA1UEChMMVGhhd3RlLCBJbmMu
MR0wGwYDVQQLExREb21haW4gVmFsaWRhdGVkIFNTTDEZMBcGA1UEAxMQVGhhd3Rl
IERWIFNTTCBDQTCCASIwDQYJKoZIhvcNAQEBBQADggEPADCCAQoCggEBAMuYyTY/
0pzYFgfUSWP5g7DoAi3MXFp0l6YT7xMT3gV8p+bKACPaOfnvE89Sxa+a48q+84LZ
iz2q4cyuiFBmoy3sYRR1SasOJPGsRFsLKKIzIHYeBmBqZwVxi7pmYhZ6s20Nx9CU
QMaMPR6SDGI0DUSJ1feJ/intGI/2mysI92qr2EiXWvSf7Qx1UiL31V6EAJ/ASg0x
d0xk0BLmDzrwocDVXB3nXy3C99Y2GNmVbkROyVgUTbaOu83eYh76W7W9GCuYrKyT
P1Ba9RQLos+2855PWs1awzYj2hqvsE3WSiIDj0MCGb3qrN3EejUyFPFyLghVQAz0
B0FBrzg3hClCslUCAwEAAaOB/DCB+TAyBggrBgEFBQcBAQQmMCQwIgYIKwYBBQUH
MAGGFmh0dHA6Ly9vY3NwLnRoYXd0ZS5jb20wEgYDVR0TAQH/BAgwBgEB/wIBADA0
BgNVHR8ELTArMCmgJ6AlhiNodHRwOi8vY3JsLnRoYXd0ZS5jb20vVGhhd3RlUENB
LmNybDAOBgNVHQ8BAf8EBAMCAQYwKQYDVR0RBCIwIKQeMBwxGjAYBgNVBAMTEVZl
cmlTaWduTVBLSS0yLTExMB0GA1UdDgQWBBSrRORd7IPH2cCFn/fhxpeQsIw/mDAf
BgNVHSMEGDAWgBR7W0XPr87Lev0xkhpqtvNG61dIUDANBgkqhkiG9w0BAQUFAAOC
AQEABLr7rLv8S1QRoy2Iszy9AG2KGraNxMGD+MdTKsEybjqBoVR92ho/OkVPNudC
sApChZegrPvlh6eDT+ixt5tYZW4mgAuSTUdVuWEWUWXpK/Fo2Vi4A4HRt2Yc07zF
pntfPsU4RnbndbSgDEvOosKpwcw2c3v7uSQkoF6n9vq7DChDnh3wTvA/2CSwIdxt
Le6/Wjv6iJx0bK8h3ZLswxXvlHUmRtamP79mSKod790n5rdRiTh9E4QMQPzQtfHg
2/lPL0ActI5HImG4TJbe8F8Rfk8R2exQRyIOxR3iZEnnaGNFOorZcfRe8W63FE0+
bxQe3FL+vN8MvSk/dvsRX2hoFQ==
-----END CERTIFICATE-----
 2 s:/C=US/O=thawte, Inc./OU=Certification Services Division/OU=(c) 2006 thawte, Inc. - For authorized use only/CN=thawte Primary Root CA
   i:/C=ZA/ST=Western Cape/L=Cape Town/O=Thawte Consulting cc/OU=Certification Services Division/CN=Thawte Premium Server CA/emailAddress=premium-server@thawte.com
-----BEGIN CERTIFICATE-----
MIIERTCCA66gAwIBAgIQM2VQCHmtc+IwueAdDX+skTANBgkqhkiG9w0BAQUFADCB
zjELMAkGA1UEBhMCWkExFTATBgNVBAgTDFdlc3Rlcm4gQ2FwZTESMBAGA1UEBxMJ
Q2FwZSBUb3duMR0wGwYDVQQKExRUaGF3dGUgQ29uc3VsdGluZyBjYzEoMCYGA1UE
CxMfQ2VydGlmaWNhdGlvbiBTZXJ2aWNlcyBEaXZpc2lvbjEhMB8GA1UEAxMYVGhh
d3RlIFByZW1pdW0gU2VydmVyIENBMSgwJgYJKoZIhvcNAQkBFhlwcmVtaXVtLXNl
cnZlckB0aGF3dGUuY29tMB4XDTA2MTExNzAwMDAwMFoXDTIwMTIzMDIzNTk1OVow
gakxCzAJBgNVBAYTAlVTMRUwEwYDVQQKEwx0aGF3dGUsIEluYy4xKDAmBgNVBAsT
H0NlcnRpZmljYXRpb24gU2VydmljZXMgRGl2aXNpb24xODA2BgNVBAsTLyhjKSAy
MDA2IHRoYXd0ZSwgSW5jLiAtIEZvciBhdXRob3JpemVkIHVzZSBvbmx5MR8wHQYD
VQQDExZ0aGF3dGUgUHJpbWFyeSBSb290IENBMIIBIjANBgkqhkiG9w0BAQEFAAOC
AQ8AMIIBCgKCAQEArKDw+4BZ1JzHpM+doVlzCRBFDA0sbmjxbFtIaElZN/wLMxnC
d3/MEC2VNBzm600JpxzSuMmXNgK3idQkXwbAzESUlI0CYm/rWt0RjSiaXISQEHoN
vXRmL2o4oOLVVETrHQefB7pv7un9Tgsp9T6EoAHxnKv4HH6JpOih2HFlDaNRe+68
0iJgDblbnd+6/FFbC6+Ysuku6QToYofeK8jXTsFMZB7dz4dYukpPymgHHRydSsbV
L5HMfHFyHMXAZ+sy/cmSXJTahcCbv1N9Kwn0jJ2RH5dqUsveCTakd9h7h1BE1T5u
KWn7OUkmHgmlgHtALevoJ4XJ/mH9fuZ8lx3VnQIDAQABo4HCMIG/MA8GA1UdEwEB
/wQFMAMBAf8wOwYDVR0gBDQwMjAwBgRVHSAAMCgwJgYIKwYBBQUHAgEWGmh0dHBz
Oi8vd3d3LnRoYXd0ZS5jb20vY3BzMA4GA1UdDwEB/wQEAwIBBjAdBgNVHQ4EFgQU
e1tFz6/Oy3r9MZIaarbzRutXSFAwQAYDVR0fBDkwNzA1oDOgMYYvaHR0cDovL2Ny
bC50aGF3dGUuY29tL1RoYXd0ZVByZW1pdW1TZXJ2ZXJDQS5jcmwwDQYJKoZIhvcN
AQEFBQADgYEAhKhMyT4qvJrizI8LsiV3xGGJiWNa1KMVQNT7Xj+0Q+pjFytrmXSe
Cajd1FYVLnp5MV9jllMbNNkV6k9tcMq+9oKp7dqFd8x2HGqBCiHYQZl/Xi6Cweiq
95OBBaqStB+3msAHF/XLxrRMDtdW3HEgdDjWdMbWj2uvi42gbCkLYeA=
-----END CERTIFICATE-----
 3 s:/C=ZA/ST=Western Cape/L=Cape Town/O=Thawte Consulting cc/OU=Certification Services Division/CN=Thawte Premium Server CA/emailAddress=premium-server@thawte.com
   i:/C=ZA/ST=Western Cape/L=Cape Town/O=Thawte Consulting cc/OU=Certification Services Division/CN=Thawte Premium Server CA/emailAddress=premium-server@thawte.com
-----BEGIN CERTIFICATE-----
MIIDJzCCApCgAwIBAgIBATANBgkqhkiG9w0BAQQFADCBzjELMAkGA1UEBhMCWkEx
FTATBgNVBAgTDFdlc3Rlcm4gQ2FwZTESMBAGA1UEBxMJQ2FwZSBUb3duMR0wGwYD
VQQKExRUaGF3dGUgQ29uc3VsdGluZyBjYzEoMCYGA1UECxMfQ2VydGlmaWNhdGlv
biBTZXJ2aWNlcyBEaXZpc2lvbjEhMB8GA1UEAxMYVGhhd3RlIFByZW1pdW0gU2Vy
dmVyIENBMSgwJgYJKoZIhvcNAQkBFhlwcmVtaXVtLXNlcnZlckB0aGF3dGUuY29t
MB4XDTk2MDgwMTAwMDAwMFoXDTIwMTIzMTIzNTk1OVowgc4xCzAJBgNVBAYTAlpB
MRUwEwYDVQQIEwxXZXN0ZXJuIENhcGUxEjAQBgNVBAcTCUNhcGUgVG93bjEdMBsG
A1UEChMUVGhhd3RlIENvbnN1bHRpbmcgY2MxKDAmBgNVBAsTH0NlcnRpZmljYXRp
b24gU2VydmljZXMgRGl2aXNpb24xITAfBgNVBAMTGFRoYXd0ZSBQcmVtaXVtIFNl
cnZlciBDQTEoMCYGCSqGSIb3DQEJARYZcHJlbWl1bS1zZXJ2ZXJAdGhhd3RlLmNv
bTCBnzANBgkqhkiG9w0BAQEFAAOBjQAwgYkCgYEA0jY2aovXwlue2oFBYo847kkE
VdbQ7xwblRZH7xhINTpS9CtqBo87L+pW46+GjZ4X9560ZXUCTe/LCaIhUdib0GfQ
ug2SBhRz1JPLlyoAnFxODLz6FVL88kRu2hFKbgifLy3j+ao6hnO2RlNYyIkFvYMR
uHM/qgeN9EJN50CdHDcCAwEAAaMTMBEwDwYDVR0TAQH/BAUwAwEB/zANBgkqhkiG
9w0BAQQFAAOBgQAmSCwWwlj66BZ0DKqqX1Q/8tfJeGBeXm43YyJ3Nn6yF8Q0ufUI
hfzJATj/Tb7yFkJD57taRvvBxhEf8UqwKEbJw8RCfbz6q1lu1bdRiBHjpIUZa4JM
pAwSremkrj/xw0llmozFyD4lt5SZu5IycQfwhl7tUCemDaYj+bvLpgcUQg==
-----END CERTIFICATE-----
---
Server certificate
subject=/O=support.nextpointhost.com/OU=Go to [https://www.thawte.com/repository/index.html/OU=Thawte](https://www.thawte.com/repository/index.html/OU=Thawte) SSL123 certificate/OU=Domain Validated/CN=support.nextpointhost.com
issuer=/C=US/O=Thawte, Inc./OU=Domain Validated SSL/CN=Thawte DV SSL CA
---
No client certificate CA names sent
---
SSL handshake has read 4886 bytes and written 319 bytes
---
New, TLSv1/SSLv3, Cipher is DHE-RSA-AES256-SHA
Server public key is 2048 bit
Secure Renegotiation IS NOT supported
Compression: NONE
Expansion: NONE
SSL-Session:
    Protocol  : TLSv1
    Cipher    : DHE-RSA-AES256-SHA
    Session-ID: 999125C8F1EA3559AE9DD65229B37A5F301F5F74B13CE685FDA82E4A4C818194
    Session-ID-ctx: 
    Master-Key: 57391BF9B13F439624D7B301892232B0116E7C328F864E52D7715A215E883CDF6907927D17583881BE906B4D6C2965C0
    Key-Arg   : None
    Start Time: 1308210040
    Timeout   : 300 (sec)
    **Verify return code: 19 (self signed certificate in certificate chain)**
---


closed


How everything is fine and I receive self signed certificate chain, because CA is not ensured by other organization or this is wrong?

---

### Post by BkkBonanza on 2011-06-16
You need to provide openssl with a valid final CA so it can verify eventually to a known local CA certificate. At least I think this is true, otherwise it will depend on trusting one found on the web (which may not be trustworthy). That is, your browser has a built in store of trusted CA certs and so it resolves down to one of them. 

And so should openssl when testing. I'm not 100% certain of this but I did  repeat your test here and get the same results, and when I told openssl to use my default local CA store it finished the chain successfully.

eg.
openssl s_client -CApath /etc/ssl/certs -host support.nextpointhost.com -port 443 -showcerts

is successful, so I believe this to be the correct way. If it can't resolve to a trusted CA then it cannot trust the chain.

As another test I checked my web site which uses a self-signed cert and it cannot finish the chain successfully even when provided with the local CApath since my (self-signed) CA cert is not in the trusted store.

---

### Post by hawkmage on 2011-06-16
I have a feeling that the Thawte CA certificates is not in the openssl CA trust directory: /etc/ssl/certs.

To add the Thawte CA certificates to the openssl CA trust directory I would first backup the directoy:
```
cd /etc/ssl
sudo tar cf save_certs.tar certs
```

Now download the Thawte CA certificates, place them in the /etc/ssl/certs directory and then run:
```
sudo c_rehash /etc/ssl/certs/
```

The c_rehash command will create the links named xxxxxxxx.#.  This is what openssl uses find the cert to match.

---

### Post by BkkBonanza on 2011-06-17
It's definitely in mine and as far as I know I have the default set.
I tested it here. When you use openssl you have to tell it explicity to use the path /etc/ssl/certs/

I see it here as "Thawte_Premium_Server_CA.pem".

As an aside I also tested with my own self-signed CA. I created the hash link manually with openssl and that works too.

---

### Post by Abadon_ on 2011-06-17
**@hawkmage** I do this before open this topic.

How I repeat steps which you suggest but result is the same Verify return code: 19 (self signed certificate in certificate chain).

**@BkkBonanza**
Thawte CAs are into /etc/ssl/certs/:

> root@www:~# ls -lah /etc/ssl/certs/Tha*
lrwxrwxrwx 1 root root 63 2010-05-30 12:53 /etc/ssl/certs/Thawte_Personal_Basic_CA.pem -> /usr/share/ca-certificates/mozilla/Thawte_Personal_Basic_CA.crt
lrwxrwxrwx 1 root root 66 2010-05-30 12:53 /etc/ssl/certs/Thawte_Personal_Freemail_CA.pem -> /usr/share/ca-certificates/mozilla/Thawte_Personal_Freemail_CA.crt
lrwxrwxrwx 1 root root 65 2010-05-30 12:53 /etc/ssl/certs/Thawte_Personal_Premium_CA.pem -> /usr/share/ca-certificates/mozilla/Thawte_Personal_Premium_CA.crt
lrwxrwxrwx 1 root root 63 2010-05-30 12:53 /etc/ssl/certs/**Thawte_Premium_Server_CA.pem -> /usr/share/ca-certificates/mozilla/Thawte_Premium_Server_CA.crt**
lrwxrwxrwx 1 root root 55 2010-05-30 12:53 /etc/ssl/certs/Thawte_Server_CA.pem -> /usr/share/ca-certificates/mozilla/Thawte_Server_CA.crt
lrwxrwxrwx 1 root root 62 2010-05-30 12:53 /etc/ssl/certs/Thawte_Time_Stamping_CA.pem -> /usr/share/ca-certificates/mozilla/Thawte_Time_Stamping_CA.crt

> root@www:~# ls -lah /etc/ssl/certs/SSL123*
-rw-r--r-- 1 root root 3,2K 2011-06-09 21:26 /etc/ssl/certs/SSL123_CA_Bundle.pem
-rwxr-xr-x 1 root root 1,6K 2011-06-10 00:00 /etc/ssl/certs/SSL123_PrimaryCA.pem
-rwxr-xr-x 1 root root 1,7K 2011-06-10 00:01 /etc/ssl/certs/SSL123_SecondaryCA.pem


Is it possible this issue to be due wrong permissions of CAs or something else?

---

### Post by BkkBonanza on 2011-06-17
See my second post up from here (#5). Your problem is you need to add 

-CApath /etc/ssl/certs 

to your openssl command. Then you get correct results.

---

