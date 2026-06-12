---
title: "Certificate Errors After Power Outage."
date: 2008-02-24
forum: Server Platforms
---

### Post by bmathis on 2008-02-24
Hello everyone. 

There was a power outage at my house today because of weather. When I got home several hours later, I proceeded to turn on my server and found the following message after logging on. I searched the web and cant really find anything on how to fix this problem. My server is running LAMP and Postfix. I cannot browse to my websites but I am able to send and receive mail. If anyone can shed some light on why this happened and how to fix it, that would be great.

Error that shows on login
```

Last login: Sat Feb 23 22:16:26 2008 from 192.168.10.69
-bash: brasil.gov.br/brasil.gov.br.crt: No such file or directory
-bash: cacert.org/class3.crt: No such file or directory
-bash: cacert.org/root.crt: No such file or directory
-bash: debconf.org/ca.crt: No such file or directory
-bash: mozilla/ABAecom_=sub.__Am._Bankers_Assn.=_Root_CA.crt: No such file or directory
-bash: mozilla/AddTrust_External_Root.crt: No such file or directory
-bash: mozilla/AddTrust_Low-Value_Services_Root.crt: No such file or directory
-bash: mozilla/AddTrust_Public_Services_Root.crt: No such file or directory
-bash: mozilla/AddTrust_Qualified_Certificates_Root.crt: No such file or directory
-bash: mozilla/America_Online_Root_Certification_Authority_1.crt: No such file or directory
-bash: mozilla/America_Online_Root_Certification_Authority_2.crt: No such file or directory
-bash: mozilla/AOL_Time_Warner_Root_Certification_Authority_1.crt: No such file or directory
-bash: mozilla/AOL_Time_Warner_Root_Certification_Authority_2.crt: No such file or directory
-bash: mozilla/Baltimore_CyberTrust_Root.crt: No such file or directory
-bash: mozilla/beTRUSTed_Root_CA-Baltimore_Implementation.crt: No such file or directory
-bash: mozilla/beTRUSTed_Root_CA.crt: No such file or directory
-bash: mozilla/beTRUSTed_Root_CA_-_Entrust_Implementation.crt: No such file or directory
-bash: mozilla/beTRUSTed_Root_CA_-_RSA_Implementation.crt: No such file or directory
-bash: mozilla/Certum_Root_CA.crt: No such file or directory
-bash: mozilla/Comodo_AAA_Services_root.crt: No such file or directory
-bash: mozilla/Comodo_Secure_Services_root.crt: No such file or directory
-bash: mozilla/Comodo_Trusted_Services_root.crt: No such file or directory
-bash: mozilla/Digital_Signature_Trust_Co._Global_CA_1.crt: No such file or directory
-bash: mozilla/Digital_Signature_Trust_Co._Global_CA_2.crt: No such file or directory
-bash: mozilla/Digital_Signature_Trust_Co._Global_CA_3.crt: No such file or directory
-bash: mozilla/Digital_Signature_Trust_Co._Global_CA_4.crt: No such file or directory
-bash: mozilla/Entrust.net_Global_Secure_Personal_CA.crt: No such file or directory
-bash: mozilla/Entrust.net_Global_Secure_Server_CA.crt: No such file or directory
-bash: mozilla/Entrust.net_Premium_2048_Secure_Server_CA.crt: No such file or directory
-bash: mozilla/Entrust.net_Secure_Personal_CA.crt: No such file or directory
-bash: mozilla/Entrust.net_Secure_Server_CA.crt: No such file or directory
-bash: mozilla/Equifax_Secure_CA.crt: No such file or directory
-bash: mozilla/Equifax_Secure_eBusiness_CA_1.crt: No such file or directory
-bash: mozilla/Equifax_Secure_eBusiness_CA_2.crt: No such file or directory
-bash: mozilla/Equifax_Secure_Global_eBusiness_CA.crt: No such file or directory
-bash: mozilla/GeoTrust_Global_CA.crt: No such file or directory
-bash: mozilla/GlobalSign_Root_CA.crt: No such file or directory
-bash: mozilla/GTE_CyberTrust_Global_Root.crt: No such file or directory
-bash: mozilla/GTE_CyberTrust_Root_CA.crt: No such file or directory
-bash: mozilla/IPS_Chained_CAs_root.crt: No such file or directory
-bash: mozilla/IPS_CLASE1_root.crt: No such file or directory
-bash: mozilla/IPS_CLASE3_root.crt: No such file or directory
-bash: mozilla/IPS_CLASEA1_root.crt: No such file or directory
-bash: mozilla/IPS_CLASEA3_root.crt: No such file or directory
-bash: mozilla/IPS_Servidores_root.crt: No such file or directory
-bash: mozilla/IPS_Timestamping_root.crt: No such file or directory
-bash: mozilla/QuoVadis_Root_CA.crt: No such file or directory
-bash: mozilla/RSA_Root_Certificate_1.crt: No such file or directory
-bash: mozilla/RSA_Security_1024_v3.crt: No such file or directory
-bash: mozilla/RSA_Security_2048_v3.crt: No such file or directory
-bash: mozilla/Security_Communication_Root_CA.crt: No such file or directory
-bash: mozilla/Sonera_Class_1_Root_CA.crt: No such file or directory
-bash: mozilla/Sonera_Class_2_Root_CA.crt: No such file or directory
-bash: mozilla/Staat_der_Nederlanden_Root_CA.crt: No such file or directory
-bash: mozilla/TC_TrustCenter__Germany__Class_2_CA.crt: No such file or directory
-bash: mozilla/TC_TrustCenter__Germany__Class_3_CA.crt: No such file or directory
-bash: mozilla/TDC_Internet_Root_CA.crt: No such file or directory
-bash: mozilla/TDC_OCES_Root_CA.crt: No such file or directory
-bash: mozilla/Thawte_Personal_Basic_CA.crt: No such file or directory
-bash: mozilla/Thawte_Personal_Freemail_CA.crt: No such file or directory
-bash: mozilla/Thawte_Personal_Premium_CA.crt: No such file or directory
-bash: mozilla/Thawte_Premium_Server_CA.crt: No such file or directory
-bash: mozilla/Thawte_Server_CA.crt: No such file or directory
-bash: mozilla/Thawte_Time_Stamping_CA.crt: No such file or directory
-bash: mozilla/UTN_DATACorp_SGC_Root_CA.crt: No such file or directory
-bash: mozilla/UTN_USERFirst_Email_Root_CA.crt: No such file or directory
-bash: mozilla/UTN_USERFirst_Hardware_Root_CA.crt: No such file or directory
-bash: mozilla/UTN-USER_First-Network_Applications.crt: No such file or directory
-bash: mozilla/UTN_USERFirst_Object_Root_CA.crt: No such file or directory
-bash: mozilla/ValiCert_Class_1_VA.crt: No such file or directory
-bash: mozilla/ValiCert_Class_2_VA.crt: No such file or directory
-bash: mozilla/Verisign_Class_1_Public_Primary_Certification_Authority.crt: No such file or directory
-bash: mozilla/Verisign_Class_1_Public_Primary_Certification_Authority_-_G2.crt: No such file or directory
-bash: mozilla/Verisign_Class_1_Public_Primary_Certification_Authority_-_G3.crt: No such file or directory
-bash: mozilla/Verisign_Class_1_Public_Primary_OCSP_Responder.crt: No such file or directory
-bash: mozilla/Verisign_Class_2_Public_Primary_Certification_Authority.crt: No such file or directory
-bash: mozilla/Verisign_Class_2_Public_Primary_Certification_Authority_-_G2.crt: No such file or directory
-bash: mozilla/Verisign_Class_2_Public_Primary_Certification_Authority_-_G3.crt: No such file or directory
-bash: mozilla/Verisign_Class_2_Public_Primary_OCSP_Responder.crt: No such file or directory
-bash: mozilla/Verisign_Class_3_Public_Primary_Certification_Authority.crt: No such file or directory
-bash: mozilla/Verisign_Class_3_Public_Primary_Certification_Authority_-_G2.crt: No such file or directory
-bash: mozilla/Verisign_Class_3_Public_Primary_Certification_Authority_-_G3.crt: No such file or directory
-bash: mozilla/Verisign_Class_3_Public_Primary_OCSP_Responder.crt: No such file or directory
-bash: mozilla/Verisign_Class_4_Public_Primary_Certification_Authority_-_G2.crt: No such file or directory
-bash: mozilla/Verisign_Class_4_Public_Primary_Certification_Authority_-_G3.crt: No such file or directory
-bash: mozilla/Verisign_RSA_Secure_Server_CA.crt: No such file or directory
-bash: mozilla/Verisign_Secure_Server_OCSP_Responder.crt: No such file or directory
-bash: mozilla/Verisign_Time_Stamping_Authority_CA.crt: No such file or directory
-bash: mozilla/Visa_eCommerce_Root.crt: No such file or directory
-bash: mozilla/Visa_International_Global_Root_2.crt: No such file or directory
-bash: quovadis.bm/QuoVadis_Root_Certification_Authority.crt: No such file or directory
-bash: signet.pl/signet_ca1_pem.crt: No such file or directory
-bash: signet.pl/signet_ca2_pem.crt: No such file or directory
-bash: signet.pl/signet_ca3_pem.crt: No such file or directory
-bash: signet.pl/signet_ocspklasa2_pem.crt: No such file or directory
-bash: signet.pl/signet_ocspklasa3_pem.crt: No such file or directory
-bash: signet.pl/signet_pca2_pem.crt: No such file or directory
-bash: signet.pl/signet_pca3_pem.crt: No such file or directory
-bash: signet.pl/signet_rootca_pem.crt: No such file or directory
-bash: signet.pl/signet_tsa1_pem.crt: No such file or directory
-bash: spi-inc.org/SPI_CA_2006-cacert.crt: No such file or directory
-bash: spi-inc.org/spi-ca.crt: No such file or directory

```

---

### Post by k_grdn on 2008-02-24
Hi,

First thing check if the directory /usr/share/ca-certificates/ exists, if not thats your problem.  A sudden power loss can corrupt disks and cause data loss.  Have you run fsck on the volume?

It's most likely that firefox is complaining because it uses certs to validate ssl certs valadated by trusted authorities like thwarte etc..
Basically when entering a https site with a cert signed by a trusted body you will not be prompted to accept the cert cause firefox has a list of sites which are trusted and if you site cert is not signed by one of these sites it's deemed as untrusted.

To resolve the problem just give firefox what it wants, re-install the certs/firefox.

Also check the rest of your disk for missing files.

Regards,

k_grdn

---

### Post by bmathis on 2008-02-24
Thanks for the reply
> First thing check if the directory /usr/share/ca-certificates/ exists, if not thats your problem.
This folder does exist and the files are present.
> A sudden power loss can corrupt disks and cause data loss.  Have you run fsck on the volume?
Thats the first thing i did and everything checks out clean.
> It's most likely that firefox is complaining because it uses certs to validate ssl certs valadated by trusted authorities like thwarte etc..
Basically when entering a https site with a cert signed by a trusted body you will not be prompted to accept the cert cause firefox has a list of sites which are trusted and if you site cert is not signed by one of these sites it's deemed as untrusted.

To resolve the problem just give firefox what it wants, re-install the certs/firefox.
This is a cli based server install, no gui, no firefox, no monitor. all administration is done via ssh.
> 
Also check the rest of your disk for missing files.
There was no missing files that I could see

If anyone else has any suggestions, please chime in... thanks again for the help.

---

### Post by k_grdn on 2008-02-24
Hi,

Are you sites ssl? are you using mod_ssl?

Regards,

k_grdn

---

### Post by bmathis on 2008-02-24
No ssl sites... its just a couple of blogs that I host for friends and my guild website for eq2

---

### Post by k_grdn on 2008-02-24
Anything in /var/log/syslog? or is the error related to the initial user logon?

---

### Post by bmathis on 2008-02-28
Sorry for responding so late. I couldnt wait too long, I just backed up everything and reloaded the server. Thanks for the help.

---

