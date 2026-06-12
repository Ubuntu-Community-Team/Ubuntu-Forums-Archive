---
title: "Setting Up SSL on LAMP"
date: 2006-07-19
forum: Server Platforms
---

### Post by sparty2809 on 2006-07-19
Ok, I think I posted this in the wrong forum last time, so here we go:

Ok, I installed the LAMP Server from the Ubuntu 6.06 disk. I got my crt file back from godaddy. Now how do I set it up? I tried putting the

```
SSLCertificateFile /etc/apache2/ssl/ssl.csr/website.csr
SSLCertificateKeyFile /etc/apache2/ssl/ssl.key/website.key
SSLCertificateChainFile /etc/apache2/ssl/ssl.crt/website.crt
```


in the ssl.conf file, but it doesn't work. I get this error: "Error Code: -12281" when I bring it up in Firefox.  The apache log says:

```
[Wed Jul 19 12:44:24 2006] [error] Init: Unable to read server certificate from file /etc/apache2/ssl/ssl.crt/ ssl.crt
 
[Wed Jul 19 12:44:24 2006] [error] SSL Library Error: 218529960 error:0D0680A8:asn1 encoding routines:ASN1_CHE CK_TLEN:wrong tag

[Wed Jul 19 12:44:24 2006] [error] SSL Library Error: 218595386 error:0D07803A:asn1 encoding routines:ASN1_ITE M_EX_D2I:nested asn1 error
```

Does anyone know a step by step process? I have found a lot on self signed ones, but I don't think it's the same steps.

---

### Post by Randomskk on 2006-07-19
Have you checked the Server Guide (look for a sticky in this section)?
That has details on how to do it, but I think the most important things for you are:
1) make sure apache is listening on port 443 (see the guide), and
2) those lines need to a virtual host, I believe the guide also covers that
3) make sure the cert file is readable by apache! Something like:
chown www-data /etc/apache2/ssl.crt
Finally, why are you getting this error? "file /etc/apache2/ssl/ssl.crt/ ssl.crt"
Do you have an ssl.crt directory or what? :/

---

