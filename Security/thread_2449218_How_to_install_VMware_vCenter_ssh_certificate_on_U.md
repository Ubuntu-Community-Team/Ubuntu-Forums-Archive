---
title: "How to install VMware vCenter ssh certificate on Ubuntu"
date: 2020-08-22
forum: Security
---

### Post by gav1 on 2020-08-22
I am using Ubuntu GUI and Chrome browser to connect to vCenter.

 

I see the error that my connection may not be private:
Your connection is not private

Attackers might be trying to steal your information from 192.168.2.123 (for example, passwords, messages or credit cards). Learn more

 
NET::ERR_CERT_AUTHORITY_INVALID

 
This article has no instructions on how to install certificates on Linux machines: VMware Knowledge Base
I downloaded the vCenter certificates to Ubuntu.


and tried to use this forum [https://askubuntu.com/questions/73287/how-do-i-install-a-root-certificate](https://askubuntu.com/questions/73287/how-do-i-install-a-root-certificate)
I tried to use the same commands on my local ubuntu machine and virtual ubuntu server were I installed GUI but it did not help.
There is no information on internet how to install vCenter certificates on ubuntu.

I run on ubuntu the following commands:

root@lab1:/home/lab1/Downloads/download/certs/win# ls

dbad4059.0.crt  dbad4059.r0.crl

root@lab1:/home/lab1/Downloads/download/certs/win# cp dbad4059.0.crt /usr/share/ca-certificates/extra/

root@lab1:/home/lab1/Downloads/download/certs/win# cd /usr/share/ca-certificates/extra

root@lab1:/usr/share/ca-certificates/extra# ls

dbad4059.0.crt

root@lab1:/usr/share/ca-certificates/extra# sudo dpkg-reconfigure ca-certificates

Updating certificates in /etc/ssl/certs...

1 added, 0 removed; done.

Processing triggers for ca-certificates (20190110ubuntu1.1) ...

Updating certificates in /etc/ssl/certs...

0 added, 0 removed; done.

Running hooks in /etc/ca-certificates/update.d...

done.

root@lab1:/usr/share/ca-certificates/extra# update-ca-certificates

Updating certificates in /etc/ssl/certs...

0 added, 0 removed; done.

Running hooks in /etc/ca-certificates/update.d...

done.

root@lab1:/usr/share/ca-certificates/extra#

 

 

root@lab1:/usr/share/ca-certificates/extra# less /etc/ca-certificates.conf

la/VeriSign_Universal_Root_Certification_Authority.crt

mozilla/Verisign_Class_3_Public_Primary_Certification_Authority_-_G3.crt

mozilla/XRamp_Global_CA_Root.crt

mozilla/certSIGN_ROOT_CA.crt

mozilla/ePKI_Root_Certification_Authority.crt

mozilla/thawte_Primary_Root_CA.crt

mozilla/thawte_Primary_Root_CA_-_G2.crt

mozilla/thawte_Primary_Root_CA_-_G3.crt

extra/dbad4059.0.crt   #this line indicates thatvCenter certificate was added to ca-certificates.conf

as it was mention here [https://askubuntu.com/questions/73287/how-do-i-install-a-root-certificate](https://askubuntu.com/questions/73287/how-do-i-install-a-root-certificate)

 

#this is a lab envirnomen and this is how the certificate looks like

oot@lab1:/usr/share/ca-certificates/extra# cat dbad4059.0.crt

-----BEGIN CERTIFICATE-----

MIIECzCCAvOgAwIBAgIJAOVFQJ3o+FTMMA0GCSqGSIb3DQEBCwUAMIGQMQswCQYD

VQQDDAJDQTEXMBUGCgmSJomT8ixkARkWB3ZzcGhlcmUxFTATBgoJkiaJk/IsZAEZ

FgVsb2NhbDELMAkGA1UEBhMCVVMxEzARBgNVBAgMCkNhbGlmb3JuaWExEjAQBgNV

BAoMCWxvY2FsaG9zdDEbMBkGA1UECwwSVk13YXJlIEVuZ2luZWVyaW5nMB4XDTIw

MDcyMDEzNDAyM1oXDTMwMDcxODEzNDAyM1owgZAxCzAJBgNVBAMMAkNBMRcwFQYK

CZImiZPyLGQBGRYHdnNwaGVyZTEVMBMGCgmSJomT8ixkARkWBWxvY2FsMQswCQYD

VQQGEwJVUzETMBEGA1UECAwKQ2FsaWZvcm5pYTESMBAGA1UECgwJbG9jYWxob3N0

MRswGQYDVQQLDBJWTXdhcmUgRW5naW5lZXJpbmcwggEiMA0GCSqGSIb3DQEBAQUA

A4IBDwAwggEKAoIBAQC/QkcJNHMxKlUr2EJRZx42YsISn8L7FssxFS2f6ppjTvt8

i4kDdLKbBQN2SbSX8FeBYneRyLMOlnZO0Hqp0qXFS6rKkjyebJSoL4Be+sPBam2M

vFmlANwfYwUWKk/hnpn5QB0scbZEJrIodAc2JRNMjJC1WUwD62OnbwNllkv4CdGl

uIJiQbk9BOFpbbvb/vJDyFgJbSB2DlX3iKJ3D9Kq7YBtIyG+iWd3CH5ST6Ae4AOL

25dIzT7XVVehkfm8gRbUslRQd+8o0JM3anh4GOuzMs5NbcH6VDRKDnZbKCoNU546

Hkg578mo3jtyNWS7OqyBPQT0RUyRgDSpaB/9lBMJAgMBAAGjZjBkMB0GA1UdDgQW

BBQMYccCS2z3eMRfSqqatMGmcVL8SjAfBgNVHREEGDAWgQ5lbWFpbEBhY21lLmNv

bYcEfwAAATAOBgNVHQ8BAf8EBAMCAQYwEgYDVR0TAQH/BAgwBgEB/wIBADANBgkq

hkiG9w0BAQsFAAOCAQEAs88XR2vKfX41m3sstxY6xaovMHOj7A1bTtbjVGKe0iBa

AoCx4QZRMMjYf+JHXovpoDEFypexSetViYB31zT/5I/8nLDFvKrZ4fkOUQqZqrPU

g3JET29uOlR+wLQ6eodEgNGO4lReSrNWxETNr3bCtWEqwUO29dlSkceMO7xsMWqY

SHPlfM99AM7EUukK7Jwv1mqsSGkg/EnDwwbPxqRn8JktUPHdHCheKBbq2AGAf7WS

1vQO5DN9eDzBAFxOr20KkbTf6a1wG2DkM4lFs9PC56mAnYRGAP+AbWkn/yABmaBX

QHhHSJE6XR98dVQFxrHNZKeYrm5ssx7Quw81/RJMEg==

-----END CERTIFICATE-----

---

### Post by EuclideanCoffee on 2020-08-22
You're likely seeing this error because the certificate authority is not trusted. You have a few ways of finding a trusted CA. The most common is to simply buy the CA. Other security experts will vet their own certificates. You can read the signature and compare it with what you have on the server manually. When you are given the invalid certificate, it will provide you a finger print. Read the finger print that you trust from either the server or from another browser. If they match, it is the same. Of course this becomes taxing on its own.

Before I can help you with automating a chain of trust, I'll need to know about your vendor, your tasks, and what you expect.

If you're okay with manually checking or ignoring the warning (fine if you trust the network completely), then there's no more work necessary.

---

### Post by gav1 on 2020-08-24
Hello Thank you very much for your reply.

I am trying to install CA certificates of vCenter VMware according to this workflow of VMware: [https://kb.vmware.com/s/article/2108294#:~:text=Active%20Directory%20domain.-,From%20a%20client%20system%20Web%20browser%2C%20go%20to%20the%20base,'vsphere%2Dclient'%20extension.&text=%2Fdownload.zip%22-,Click%20the%20Download%20trusted%20root%20CA%20certificates%20link%20at%20the,right%20and%20download%20the%20file.](https://kb.vmware.com/s/article/2108294#:~:text=Active%20Directory%20domain.-,From%20a%20client%20system%20Web%20browser%2C%20go%20to%20the%20base,'vsphere%2Dclient'%20extension.&text=%2Fdownload.zip%22-,Click%20the%20Download%20trusted%20root%20CA%20certificates%20link%20at%20the,right%20and%20download%20the%20file.)

It says how to install certificates on Windows, but for Linux it says to follow official instructions of Ubuntu. I did not find any instructions of Ubuntu for vCenter. 

I was able to install this certificate on Firefox, and Firefox now shows no connection error.

Your question: [COLOR=#000000]Before I can help you with automating a chain of trust, I'll need to know about your vendor, your tasks, and what you expect.
[/COLOR]This is my home lab environment. I am running vCenter 7 on ESXi 6.7. ESXi 6.7 is installed on server  DELL T330

I failed to install vCenter certificates on two Ubuntu machines. First one is installed on my laptop. Second one is a virtual Ubuntu server which is installed on the same ESXi the vCenter is installed.   I installed Graphical User interface on a virtual Ubuntu Server.

My purpose is education and learn more about VMware products.

Expected behavior: After installation of vCenter certificates on Ubuntu,  I expect to not see any warning message in Chrome.

---

### Post by EuclideanCoffee on 2020-08-24
That is odd. After the steps you've taken, the certificate should be trusted. Have you tried rebooting?

I was going to suggest reformatting or adding to a directory or updating your certs, but it appears you've done that.

---

