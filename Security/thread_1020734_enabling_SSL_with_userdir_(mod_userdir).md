---
title: "enabling SSL with userdir (mod_userdir)"
date: 2008-12-24
forum: Security
---

### Post by bhartsb on 2008-12-24
I want to have SSL enabled for userdir. I've have generated a certificate, enabled SSL modules, and added to ssl.conf:
SSLEngine On
SSL_CertificateFile /etc/ssl/private/mycert.pem

once I add the lines above I can't access via https and then http stops working.  I'm not using Virtual Hosts only userdir.

---

