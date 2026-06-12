---
title: "SSL Directives"
date: 2011-11-27
forum: Server Platforms
---

### Post by rwfnetworking on 2011-11-27
I'm running Ubuntu 11.10 with OpenSSL and having a heck of a time figuring where to place the SSL Directives that point to my server certificates? I have tried the ports.conf, http.conf, httpd.conf and the sites-enabled default and sites-available. After I have the directives in place apache will not start, I usually get an error message in the Apache log that states I cannot use "SSLEngine on". Below is what I add. From what I have read these should be placed in the sites-available\default-ssl

SSLEngine on
SSLOptions +FakeBasicAuth +ExportCertData +StrictRequire
SSLCertificateFile /etc/ssl/certs/server.crt
SSLCertificateKeyFile /etc/ssl/private/server.key 


Am I missing something?


Thanks,

Robert

---

