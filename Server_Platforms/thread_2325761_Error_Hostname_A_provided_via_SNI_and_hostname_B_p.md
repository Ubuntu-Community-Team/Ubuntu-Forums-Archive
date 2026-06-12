---
title: "Error: Hostname A provided via SNI and hostname B provided via HTTP are different"
date: 2016-05-25
forum: Server Platforms
---

### Post by leo39 on 2016-05-25
Dear all,

I have an Ubuntu Server 14.04 LTS with Apache 2 configured as http/https proxy.
I have a valid wildcard certificate for the domain and multiple name based Virtualhosts with SSL, configured as in the following example:

  <VirtualHost 192.168.0.1:443>
    ServerName name.domain.it
    ServerAlias name.domain.it
    ProxyPass / [http://internalhost.domain.it/](http://internalhost.domain.it/)
    ProxyPassReverse / [http://internalhost.domain.it/](http://internalhost.domain.it/)
    ErrorLog ${APACHE_LOG_DIR}/error.log
    CustomLog ${APACHE_LOG_DIR}/custom_log combined
    SSLEngine on
    SSLProtocol all -SSLv2 -SSLv3
    SSLCipherSuite ALL:!DH:!EXPORT:!RC4:+HIGH:+MEDIUM:!LOW:!aNULL:!eNULL
    SSLCertificateFile /path/to/my/certificate.crt
    SSLCertificateKeyFile /path/to/my/private_key.key
    SSLCertificateChainFile /path/to/my/sub.class2.server.ca.pem
</VirtualHost>

For http all works very fine, but with https I have the following error:


 a.domain.it and b.domain.it are both CNAME record
When I open the site [https://a.domain.it/](https://a.domain.it/), the  connection is established to the server. 
After when I try to open [https://b.domain.it/](https://b.domain.it/), sometime (4/5 times every 10 attempts ) apache returns a 400 Bad Request, and an error appears in the error.log file:

 
AH02032: Hostname a.doamin.it provided via SNI and hostname b.domain.it provided via HTTP are different

If I try to open again the site [https://a.domain.it/](https://a.domain.it/) apache returns a 400 Bad Request,also for thi site and the following error appears in the error.log file:

AH02032: Hostname b.doamin.it provided via SNI and hostname a.domain.it provided via HTTP are different


On all https sites I have this problem randomly.

Have you any suggestions?

---

