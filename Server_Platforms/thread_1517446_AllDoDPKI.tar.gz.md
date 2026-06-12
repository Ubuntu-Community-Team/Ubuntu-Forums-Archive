---
title: "AllDoDPKI.tar.gz"
date: 2010-06-25
forum: Server Platforms
---

### Post by tuxrtfm on 2010-06-25
Is there anyone who as an old copy of this file used for the DOD CAC. I would really like to be able to re-setup machine login using the CAC.  I would greatly appreciate any help thanks.


Thanks in advance,
TuxRTFM


PS for refrence see this site:
"https://help.ubuntu.com/community/CommonAccessCard"


> This will take care of the CAC Certs needed by your system: NOTE: Link currently does not work, searching for alternate url

wget --no-check-certificate [https://airborne.nrl.navy.mil/PKI/AllDoDPKI.tar.gz](https://airborne.nrl.navy.mil/PKI/AllDoDPKI.tar.gz)
sudo mv AllDoDPKI.tar.gz /etc/pam_pkcs11/cacerts/
cd /etc/pam_pkcs11/cacerts/
sudo tar -zxvf AllDoDPKI.tar.gz
rm AllDoDPKI.tar.gz 

---

### Post by ken_23434 on 2010-08-13
I have not set up a computer running Linux to use a CAC yet.
 
However, ActivClient now makes a version of their software that works on Linux.  I just got my copy of it and was reading through the install manual for it.
 
My understanding is that the software is free to all DOD employees.  You would just need to request it via your commands IT department.

---

