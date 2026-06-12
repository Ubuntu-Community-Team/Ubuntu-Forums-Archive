---
title: "OpenSwan+certutil"
date: 2012-05-11
forum: Security
---

### Post by gubkabob on 2012-05-11
Hello All!
 
I install on my system openswan and certutil pkg.
I have own cert cert.p12. Next, i make DB :
# certutil -N -d /etc/ipsec.d/
Next i install cert in ipsec.d dir
# pk12util -i cert.p12 -d /etc/ipsec.d/
And next step
# certutil -K -d /etc/ipsec.d/
# certutil -L -d /etc/ipsec.d/
All work fine, i can see my cert and my rsa key.
I make change in my ipsec.conf and ipsec.secret...some ipsec.secrets @fkdn: RSA "cert - CA" and "cert - CA" to ipsec.conf lefcert section. Next i start ipsec and in auth.log see :
 
loading certificate from cert - CA. could not open host cert file /etc/ipsec.d/certs/cert - CA
 
loading secrets from "/etc/ipsec.d/private/cert - CA" could not open private key file "/etc/ipsec.d/private/cert - CA"
 
:(:(:confused:
 
Why ipsec trying to find certificate and rsa key in certs and private dir ?
Why no use nsdb ?
How i can change it ?
thx, and sry for my english.

---

