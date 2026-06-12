---
title: "google-earth crash twice and open at third times!"
date: 2016-04-17
forum: Ubuntu Development Version
---

### Post by valereguerin on 2016-04-17
hello community,

```
 freeman@Sniper-one:~$ google-earth
[0417/083250:ERROR:net_util.cc(2195)] Not implemented reached in bool net::HaveOnlyLoopbackAddresses()
[0417/083250:ERROR:x509_certificate_nss.cc(730)] CERT_PKIXVerifyCert for www.google.com failed err=-8181
[0417/083250:ERROR:x509_certificate_nss.cc(730)] CERT_PKIXVerifyCert for kh.google.com failed err=-8181
[0417/083250:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[0417/083250:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[0417/083250:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[0417/083250:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[0417/083250:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[0417/083250:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
```

for open Google-earth : crash two times and open it.......

---

### Post by Smask on 2016-04-17
Do you run G.E. with the provided Qt libraries or are you using AmirPli's specially compiled libraries? The Qt libraries that Google includes  are buggy as hell.

Here is a modified G.E. [package]("https://drive.google.com/file/d/0Bx0YZ3Xi3rgTLXotTnRndVVkOTA/view?usp=sharing") that Alchemist251 made that includes AmirPli's libraries. (64 bit only)

Other than that, you'll have to ask for help at the Google Maps and Earth forum.

---

### Post by valereguerin on 2016-04-18
update package today ! it's right now ! thanks for help:D

---

### Post by Smask on 2016-04-19
Tip: G.E. can still crash, because the integrated browser borks on javascript-heavy pages. You can work around this by loading all the pages in a external browser.

---

### Post by valereguerin on 2016-05-09
Thanks !

---

### Post by cariboo on 2016-05-09
This thread is about problems with 16.04, we are now testing 16.10. Thread closed.

---

