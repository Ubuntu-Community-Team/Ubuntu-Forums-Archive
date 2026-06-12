---
title: "Importing a root certificate"
date: 2020-05-27
forum: Security
---

### Post by eliyahujerusalem on 2020-05-27
Please note, I plan to turn this into a tutorial when I get it solved, which is the reason for the language used. IF YOU ARE READING THIS THREAD, DO NOT DO WHAT I'VE DONE because it doesn't work. (hopefully, I'll be able to post a working tutorial when this thread is closed.)

Also, please note, I'm aware of the privacy and tracking issues inherit in installing this certificate. 



I needed to install the Internet Rimon on Ubuntu  20.04 LTS. 
Please note, I use “Rimon Classic.”
I did an ISO install of Ubuntu LTS 20.04 and needed to import Internet Rimon’s myca.crt into ca-certificates.conf. 
Download the certificate from Internet Rimon: 
```
foo@foo-ubuntu-lts:~$ wget [https://212.76.127.4/stlib/certificate/myca.crt]("https://212.76.127.4/stlib/certificate/myca.crt")
foo@foo-ubuntu-lts:~$ sudo cp ~/Downloads/myca.crt /usr/share/ca-certificates/extra/myca.crt
foo@foo-ubuntu-lts:~$ sudo update-ca-certificates
Updating certificates in /etc/ssl/certs...
0 added, 0 removed; done.
Running hooks in /etc/ca-certificates/update.d...
Updating Mono key store
Mono Certificate Store Sync - version 6.8.0.105
Populate Mono certificate store from a concatenated list of certificates.
Copyright 2002, 2003 Motus Technologies. Copyright 2004-2008 Novell. BSD licensed.

Importing into legacy system store:
I already trust 128, your new list has 128
Import process completed.

Importing into BTLS system store:
I already trust 128, your new list has 128
Import process completed.
Done
done.
```

```
sudo nano /etc/ca-certificates.conf

```Make sure the last line reads extra/myca.crt and not !extra/myca.crt

However, when i try to run snap, i get 

```
foo@foo-ubuntu-lts~$ sudo snap install deezer-unofficial-player
[sudo] password for foo: 
error: cannot perform the following tasks:
- Download snap "deezer-unofficial-player" (6) from channel "stable" (Get [https://canonical-bos01.cdn.snapcraft.io/download-origin/canonical-lgw01/nTplSOv0pwWSH6ALvdHSSXOoyUvD1jjV_6.snap?token=1590580800_854c0fa765f4e6c396df3d2c76f505f035c2e2f6&interactive=1:](https://canonical-bos01.cdn.snapcraft.io/download-origin/canonical-lgw01/nTplSOv0pwWSH6ALvdHSSXOoyUvD1jjV_6.snap?token=1590580800_854c0fa765f4e6c396df3d2c76f505f035c2e2f6&interactive=1:) x509: certificate signed by unknown authority)
- Download snap "gnome-3-28-1804" (116) from channel "stable" (Get [https://canonical-bos01.cdn.snapcraft.io/download-origin/canonical-lgw01/TKv5Fm000l4XiUYJW9pjWHLkCPlDbIg1_116.snap?tok](https://canonical-bos01.cdn.snapcraft.io/download-origin/canonical-lgw01/TKv5Fm000l4XiUYJW9pjWHLkCPlDbIg1_116.snap?tok)
```

However, 
```
foo@foo-ubuntu-lts~$ sudo apt install mlocate
[sudo] password for foo: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Suggested packages:
  nocache
The following NEW packages will be installed:
  mlocate
0 upgraded, 1 newly installed, 0 to remove and 34 not upgraded.
Need to get 0 B/50.1 kB of archives.
After this operation, 258 kB of additional disk space will be used.
Selecting previously unselected package mlocate.
(Reading database ... 188958 files and directories currently installed.)
Preparing to unpack .../mlocate_0.26-3ubuntu3_amd64.deb ...
Unpacking mlocate (0.26-3ubuntu3) ...
Setting up mlocate (0.26-3ubuntu3) ...
update-alternatives: using /usr/bin/mlocate to provide /usr/bin/locate (locate) in auto mode
Adding group `mlocate' (GID 133) ...
Done.
Initializing mlocate database; this may take some time... done
Processing triggers for man-db (2.9.1-1) ...
```

Try to address "rehash: warning: skipping myca.pem,it does not contain exactly one certificate or CRL”
so 
```
foo@foo-ubuntu-lts:~$ sudo keytool -printcert -file /etc/ssl/certs/myca.pem 
Owner: EMAILADDRESS=support@netspark.com, CN=www.netspark.com, OU=Netspark RIM, O=Netspark, L=New York, ST=New York, C=US
Issuer: EMAILADDRESS=support@netspark.com, CN=www.netspark.com, OU=Netspark RIM, O=Netspark, L=New York, ST=New York, C=US
Serial number: b7484333ebb094c2
Valid from: Thu Jul 14 17:06:50 IDT 2016 until: Wed Jul 09 17:06:50 IDT 2036
Certificate fingerprints:
     SHA1: 1E:CF:5F:F1:EC:B6:6B:61:1F:7E:CA:DA:B6:EA:97:9C:02:E2:24:C6
     SHA256: 77:61:78:39:F4:EE:DB:0E:79:B9:14:24:51:B5:26:57:0D:01:57:A4:29:3C:EC:C6:7E:B3:32:7D:FA:0C:5D:58
Signature algorithm name: SHA512withRSA
Subject Public Key Algorithm: 4096-bit RSA key
Version: 3

Extensions: 

#1: ObjectId: 1.3.6.1.5.5.7.1.1 Criticality=false
AuthorityInfoAccess [
  [
   accessMethod: ocsp
   accessLocation: URIName: [http://ocsp.netspark.com](http://ocsp.netspark.com)
]
]

#2: ObjectId: 2.5.29.35 Criticality=false
AuthorityKeyIdentifier [
KeyIdentifier [
0000: 1D 9D C6 15 93 95 B0 46   02 96 43 56 C0 C6 22 7D  .......F..CV..".
0010: C5 03 2F A5                                        ../.
]
]

#3: ObjectId: 2.5.29.19 Criticality=true
BasicConstraints:[
  CA:true
  PathLen:2147483647
]

#4: ObjectId: 2.5.29.15 Criticality=true
KeyUsage [
  DigitalSignature
  Key_CertSign
  Crl_Sign
]

#5: ObjectId: 2.5.29.14 Criticality=false
SubjectKeyIdentifier [
KeyIdentifier [
0000: 1D 9D C6 15 93 95 B0 46   02 96 43 56 C0 C6 22 7D  .......F..CV..".
0010: C5 03 2F A5                                        ../.
]
]
```

Based on something I read in a forum I tried 
```
foo@foo-ubuntu-lts~$ sudo apt-get install --reinstall openssl
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 34 not upgraded.
Need to get 621 kB of archives.
After this operation, 0 B of additional disk space will be used.
Get:1 [http://il.archive.ubuntu.com/ubuntu](http://il.archive.ubuntu.com/ubuntu) focal/main amd64 openssl amd64 1.1.1f-1ubuntu2 [621 kB]
Fetched 621 kB in 0s (1,641 kB/s)
(Reading database ... 189321 files and directories currently installed.)
Preparing to unpack .../openssl_1.1.1f-1ubuntu2_amd64.deb ...
Unpacking openssl (1.1.1f-1ubuntu2) over (1.1.1f-1ubuntu2) ...
Setting up openssl (1.1.1f-1ubuntu2) ...
Processing triggers for man-db (2.9.1-1) ...
foo@foo-ubuntu-lts:~$ sudo snap install deezer-unofficial-player
error: cannot perform the following tasks:
- Download snap "deezer-unofficial-player" (6) from channel "stable" (Get [https://canonical-lcy01.cdn.snapcraft.io/download-origin/canonical-lgw01/nTplSOv0pwWSH6ALvdHSSXOoyUvD1jjV_6.snap?interactive=1&token=1590580800_854c0fa765f4e6c396df3d2c76f505f035c2e2f6:](https://canonical-lcy01.cdn.snapcraft.io/download-origin/canonical-lgw01/nTplSOv0pwWSH6ALvdHSSXOoyUvD1jjV_6.snap?interactive=1&token=1590580800_854c0fa765f4e6c396df3d2c76f505f035c2e2f6:) x509: certificate signed by unknown authority)
- Download snap "gnome-3-28-1804" (116) from channel "stable" (Get [https://canonical-bos01.cdn.snapcraft.io/download-origin/canonical-lgw01/TKv5Fm000l4XiUYJW9pjWHLkCPlDbIg1_116.snap?token=1590580800_e898c844b17bd39c00b74a023966f04b72688f30&interactive=1:](https://canonical-bos01.cdn.snapcraft.io/download-origin/canonical-lgw01/TKv5Fm000l4XiUYJW9pjWHLkCPlDbIg1_116.snap?token=1590580800_e898c844b17bd39c00b74a023966f04b72688f30&interactive=1:) x509: certificate signed by unknown authority)up openssl (1.1.1f-1ubuntu2) ...
Processing triggers for man-db (2.9.1-1) ...
foo@foo-ubuntu-lts:~$ sudo snap install deezer-unofficial-player
error: cannot perform the following tasks:
- Download snap "deezer-unofficial-player" (6) from channel "stable" (Get [https://canonical-lcy01.cdn.snapcraft.io/download-origin/canonical-lgw01/nTplSOv0pwWSH6ALvdHSSXOoyUvD1jjV_6.snap?interactive=1&token=1590580800_854c0fa765f4e6c396df3d2c76f505f035c2e2f6:](https://canonical-lcy01.cdn.snapcraft.io/download-origin/canonical-lgw01/nTplSOv0pwWSH6ALvdHSSXOoyUvD1jjV_6.snap?interactive=1&token=1590580800_854c0fa765f4e6c396df3d2c76f505f035c2e2f6:) x509: certificate signed by unknown authority)
- Download snap "gnome-3-28-1804" (116) from channel "stable" (Get [https://canonical-bos01.cdn.snapcraft.io/download-origin/canonical-lgw01/TKv5Fm000l4XiUYJW9pjWHLkCPlDbIg1_116.snap?token=1590580800_e898c844b17bd39c00b74a023966f04b72688f30&interactive=1:](https://canonical-bos01.cdn.snapcraft.io/download-origin/canonical-lgw01/TKv5Fm000l4XiUYJW9pjWHLkCPlDbIg1_116.snap?token=1590580800_e898c844b17bd39c00b74a023966f04b72688f30&interactive=1:) x509: certificate signed by unknown authority)



```
Can anyone spot what the issue is?

---

### Post by TheFu on 2020-05-27
Hey eliyahujerusalem!  Glad you made it over here from IRC!

Would be helpful if you could edit the post above and use "code tags" for all terminal/CLI/shell output.  "Advanced Editor", the choose the '#' like you would to quote or bold words.

So others know and don't need to go over the MiTM and privacy issues, this is a specific, desired, filter by the OP offered by the ISP. It isn't a govt mandated thing.

**There are some smart people here. They will figure it out.**

I'm sorta surprised that getting the CA, perhaps needing a format change, dropping it into the correct directory isn't enough.  [https://www.techrepublic.com/article/how-to-install-ca-certificates-in-ubuntu-server/](https://www.techrepublic.com/article/how-to-install-ca-certificates-in-ubuntu-server/) is what I'd expect was needed.  
```
sudo cp CERTIFICATE.crt /usr/local/share/ca-certificate
# Convert from PEM
openssl x509 -outform der -in CERTIFICATE.pem -out CERTIFICATE.crt
# Tell the system about the new cert
sudo update-ca-certificates
```
Shouldn't need to sign anything, the mlocate stuff isn't anything needed for this issue, but **locate** is handy.

Would be helpful if you included a link to the ISP's instructions, even if not for Linux.

Good luck.

---

### Post by eliyahujerusalem on 2020-07-01
If you came across this thread because you had the same problem the solution is:
Call Bezek and get a second tashtit. 
I did not succeed in doing this.

---

### Post by TheFu on 2020-07-01
> **eliyahujerusalem said:**
> If you came across this thread because you had the same problem the solution is:
**Call Bezek and get a second tashtit. **
I did not succeed in doing this.

Can this line be translated? Is Bezek an ISP and tashtit an "operator"?  The sentence seems very odd in English, so there must be a translation failure.

---

