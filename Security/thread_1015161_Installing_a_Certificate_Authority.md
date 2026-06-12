---
title: "Installing a Certificate Authority"
date: 2008-12-18
forum: Security
---

### Post by Jmoretti on 2008-12-18
I need to install a CA on this server so a website will support SSL.  The server does not have a GUI interface and I am not sure where to get started.  I am helping someone out who had this server installed for him.  He is not a linux person and I have only worked with the GUI Linux interface.  We need help getting started.  Any help will be greatly appreciated.
Thank you,
Jmoretti

---

### Post by cdenley on 2008-12-18
> **Jmoretti said:**
> I need to install a CA on this server so a website will support SSL.  The server does not have a GUI interface and I am not sure where to get started.  I am helping someone out who had this server installed for him.  He is not a linux person and I have only worked with the GUI Linux interface.  We need help getting started.  Any help will be greatly appreciated.
Thank you,
Jmoretti

What version of ubuntu are you running?
```

cat /etc/lsb-release

```
[https://help.ubuntu.com/8.04/serverguide/C/httpd.html#https-configuration](https://help.ubuntu.com/8.04/serverguide/C/httpd.html#https-configuration)
Follow this guide, except add the "SSLCertificateChainFile" option pointed to the other file provided by your CA.

---

