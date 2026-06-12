---
title: "Apache and TLSv1 and weak ciphers"
date: 2016-12-22
forum: Server Platforms
---

### Post by doeners on 2016-12-22
Hi All,

I'm trying to secure my website running ubuntu 16.04 and apache2. 
I want no weak ciphers om https site. But it looks apache is unable to disable TLSv1 and some weak ciphers.
Especially TLS_RSA_WITH_3DES_EDE_CBC_SHA 
My ssl.conf contains the following SSL statements

        SSLCipherSuite EECDH+AESGCM:EDH+AESGCM:AES256+EECDH:AES256+EDH
        SSLHonorCipherOrder on
        SSLProtocol all -SSLv2 -SSLv3 -TLSv1


However when is scan with nmap i still see TLSv1 is available as well as the weak "TLS_RSA_WITH_3DES_EDE_CBC_SHA (rsa 2048) - C"  cipher.

How to disable TLSv1 and the weak cipher ??

Thanks!

---

### Post by ajgreeny on 2016-12-22
*Thread moved to **Server Platforms**.* which is more appropriate for the problem and should be a better fit.

---

### Post by CharlesA on 2016-12-23
Hi, it looks like you are using the same ciphers are here: [https://cipherli.st/](https://cipherli.st/)

Have you already restarted or reloaded apache?

---

### Post by doeners on 2017-01-05
Sorry for the late response. But yes is have restarted everything including the whole box.

---

