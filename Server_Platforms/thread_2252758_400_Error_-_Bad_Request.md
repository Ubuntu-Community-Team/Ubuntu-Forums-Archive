---
title: "400 Error - Bad Request"
date: 2014-11-14
forum: Server Platforms
---

### Post by kernelles on 2014-11-14
I've installed LAMP on 14.04, and I can access it over http and https inside my network, but when I try to access it over the internet (dyndns), I get 400 Bad Request. Firewall is open, ports are forwarded, and ssh is working fine, so everything is ruled out but apache (2.4.7). Does anyone know what could cause this?

---

### Post by nerdtron on 2014-11-14
What is in the apache logs when you get 400 errors on the browser?

---

### Post by kernelles on 2014-11-15
> **nerdtron said:**
> What is in the apache logs when you get 400 errors on the browser?

[Sat Nov 15 03:18:41.977431 2014] [ssl:warn] [pid 1849] AH01906: RSA server certificate is a CA certificate (BasicConstraints: CA == TRUE !?)
[Sat Nov 15 03:18:42.056201 2014] [ssl:warn] [pid 1850] AH01906: RSA server certificate is a CA certificate (BasicConstraints: CA == TRUE !?)
[Sat Nov 15 03:18:42.060974 2014] [mpm_prefork:notice] [pid 1850] AH00163: Apache/2.4.7 (Ubuntu) PHP/5.5.9-1ubuntu4.5 OpenSSL/1.0.1f configured -- resuming normal operations
[Sat Nov 15 03:18:42.061060 2014] [core:notice] [pid 1850] AH00094: Command line: '/usr/sbin/apache2'

---

