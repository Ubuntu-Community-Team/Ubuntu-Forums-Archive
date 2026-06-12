---
title: "adding debian/removing debian after todays updates"
date: 2016-02-11
forum: Ubuntu Development Version
---

### Post by ventrical on 2016-02-11
Anyone have any idea what this is/ I haven't seen it happen before.

```


Adding debian:CA_WoSign_ECC_Root.pem
Adding debian:Certification_Authority_of_WoSign_G2.pem
Adding debian:Certinomis_-_Root_CA.pem
Adding debian:OISTE_WISeKey_Global_Root_GB_CA.pem
Adding debian:TÜRKTRUST_Elektronik_Sertifika_Hizmet_Sa&#287;lay&#305;c&#305;s&#305;_H5.pem
Adding debian:TÜRKTRUST_Elektronik_Sertifika_Hizmet_Sa&#287;lay&#305;c&#305;s&#305;_H6.pem
Removing debian:Entrust.net_Secure_Server_CA.pem
Removing debian:GTE_CyberTrust_Global_Root.pem
Removing debian:RSA_Root_Certificate_1.pem
Removing debian:Thawte_Premium_Server_CA.pem
Removing debian:Thawte_Server_CA.pem
Removing debian:ValiCert_Class_1_VA.pem
Removing debian:ValiCert_Class_2_VA.pem
Removing debian:A-Trust-nQual-03.pem
Removing debian:Buypass_Class_3_CA_1.pem
Removing debian:ComSign_Secured_CA.pem
Removing debian:Digital_Signature_Trust_Co._Global_CA_1.pem
Removing debian:Digital_Signature_Trust_Co._Global_CA_3.pem
Removing debian:SG_TRUST_SERVICES_RACINE.pem
Removing debian:TC_TrustCenter_Class_2_CA_II.pem
Removing debian:TC_TrustCenter_Universal_CA_I.pem
Removing debian:TURKTRUST_Certificate_Services_Provider_Root_1.pem
Removing debian:TURKTRUST_Certificate_Services_Provider_Root_2.pem
Removing debian:UTN_DATACorp_SGC_Root_CA.pem
Removing debian:Verisign_Class_4_Public_Primary_Certification_Authority_-_G3.pem
Removing debian:spi-cacert-2008.pem
done.
done.
ventrical@ventrical-MS-7850:~$ 

```

---

### Post by QDR06VV9 on 2016-02-11
I have always heard it to be the effect of a manual intervention...But don't really know in this one though?
> A note to newer users, the certificate upgrade message needs you to  manually continue the upgrade by pressing "q" (to quit the message),  then the upgrade continues.
Seen this a few years back and the above worked then.
Source  [https://forums.bunsenlabs.org/viewtopic.php?id=1156](https://forums.bunsenlabs.org/viewtopic.php?id=1156)
Regards

---

### Post by ventrical on 2016-02-12
It only happens on xenial mate-desktop yesterday.regards..

---

### Post by grahammechanical on 2016-02-12
> It only happens on xenial mate-desktop yesterday.regards..

Ah! The devs are pulling packages directly from Debian. Ubuntu devs usually re-label packages with a ubuntu name and a number value so that they can track bugs back to particular packages.

Regards.

---

### Post by dave0109 on 2016-02-13
They are root certificates, used to authenticate secure connections like HTTPS, or secure messages like S/MIME (look up X.509 certificate chains for more information).  Same as what you'll see in Firefox's Certificate Authorities list, but perhaps a different list stored elsewhere for the O/S.  That's the "what".  I've no idea about the "why" :)

---

### Post by QDR06VV9 on 2016-02-13
> **dave0109 said:**
> They are root certificates, used to authenticate secure connections like HTTPS, or secure messages like S/MIME (look up X.509 certificate chains for more information).  Same as what you'll see in Firefox's Certificate Authorities list, but perhaps a different list stored elsewhere for the O/S.  That's the "what".  I've no idea about the "why" :)

+1 
I think graham's answer might shed the light on the what!:D
The only difference between what happened with mine and ventrical's is mine would not complete the update til i hit the "q" but ventrical's appears to have completed with no interaction from the user..
Kind Regards

---

### Post by ventrical on 2016-02-14
> **runrickus said:**
> +1 
I think graham's answer might shed the light on the what!:D
The only difference between what happened with mine and ventrical's is mine would not complete the update til i hit the "q" but ventrical's appears to have completed with no interaction from the user..
Kind Regards

btw ...I have proposed repos enabled on that machine. I'll look at it again.

---

### Post by ventrical on 2016-02-18
This appears to have resolved itself.  Mate has been getting monster updates as of late.

Regards..

---

