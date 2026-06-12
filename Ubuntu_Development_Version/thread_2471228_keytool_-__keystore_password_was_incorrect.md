---
title: "keytool -  keystore password was incorrect"
date: 2022-01-24
forum: Ubuntu Development Version
---

### Post by Andrew_Welham on 2022-01-24
I'm trying to use a script from the internet to update tp-link Omada certificates, using lest encrypt certs.

The script does not work and i've pulled it apart to find out why

Thee are two main lines om the script (BTW the passwords are dummy passwords for this post)

openssl pkcs12 -export -in fullchain.pem -inkey privkey.pem -name eap -out keystore.p12 -password pass:myeapc

The password being myeapc

then 
keytool -storetype jks -importkeystore -destkeypass tplink -deststorepass tplink -destkeystore eap.keystore -srckeystore keystore.p12 -srcstoretype PKCS12 -srcstorepass myeapc

again the same passwd


the destination store does not even need to exist so its password should not matter tplink 

I keep getting keytool error: java.io.IOException: keystore password was incorrect  (the same happens if i enter the password manually

The only strange this is i am using ubuntu - jammy

Any ideas ?


Kind Regards
Andrew

---

### Post by Andrew_Welham on 2022-01-24
found it its a bug in Jammy, will report. works in focal

---

### Post by deadflowr on 2022-01-24
*Thread moved to **Ubuntu Development Version***

I see they are in the midst of upgrading openssl to 3.0 for 22.04, so I wonder if that has any affect on what you are doing.
See: [https://discourse.ubuntu.com/t/openssl-3-0-transition-plans/24453]("https://discourse.ubuntu.com/t/openssl-3-0-transition-plans/24453")

---

