---
title: "Freeradius differenciating different certificates"
date: 2015-07-21
forum: Server Platforms
---

### Post by Sean_OLeary on 2015-07-21
I have built and tested a freeradius server using eap-tls authentication and created a number of certificates. However, I want to be able to deny one certificate if it comes from one subnet but allow it if it comes from another. Example: CertStudent from ip 10.100.0.0/24, accept, CertStaff from ip 10.100.0.0/24. Am I going about this incorrectly? As far as my wireless controllers all I can do is pass them to a Radius server and not much else.

---

