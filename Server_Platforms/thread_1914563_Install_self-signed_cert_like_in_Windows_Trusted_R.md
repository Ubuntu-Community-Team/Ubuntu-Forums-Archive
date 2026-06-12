---
title: "Install self-signed cert like in Windows Trusted Root CA"
date: 2012-01-24
forum: Server Platforms
---

### Post by Sergius14 on 2012-01-24
Hi, we maked a custom self-signed certificat and successfully implemented in Apache.

Of course, browsers fails by default to trust in this certificate and invite the user to validate it.

On Windows you can install your own certificate into the Trusted Root CA (Firefox for ex. has their own DB, but thats another story...).

[http://blogs.technet.com/b/sbs/archive/2007/04/10/installing-a-self-signed-certificate-as-a-trusted-root-ca-in-windows-vista.aspx](http://blogs.technet.com/b/sbs/archive/2007/04/10/installing-a-self-signed-certificate-as-a-trusted-root-ca-in-windows-vista.aspx)


Is there any package or some place to install our custom certificates in Ubuntu?


Regards,

---

### Post by Sergius14 on 2012-01-24
I already found very good threads..


[http://blog.avirtualhome.com/2010/02/02/adding-ssl-certificates-to-google-chrome-linux-ubuntu/](http://blog.avirtualhome.com/2010/02/02/adding-ssl-certificates-to-google-chrome-linux-ubuntu/)

[http://superuser.com/questions/54615/how-to-install-a-ca-key-self-signed-ssl-on-ubuntu](http://superuser.com/questions/54615/how-to-install-a-ca-key-self-signed-ssl-on-ubuntu)

I tried to import our self-signed buts failed:

```
certutil: function failed: security library: bad database.
```

I'm going to try with CACerts, to unify them in one entity.

Importing the CACERT root.crt into  /etc/ssl/certs/ is enough?

---

