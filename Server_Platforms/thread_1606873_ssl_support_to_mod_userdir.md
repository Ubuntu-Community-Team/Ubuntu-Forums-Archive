---
title: "ssl support to mod_userdir"
date: 2010-10-27
forum: Server Platforms
---

### Post by sarte on 2010-10-27
Hi

just set up apache on my multiuser dev-server. Got ssl, userdir and apache running smoothly, but now I'm wondering if it's possible to add https support for every user? (so there would be [http://server/~user/](http://server/~user/) and [https://server/~user/](https://server/~user/))

This is probably done through apaches conf files, but because I'm new with apache I really don't know where to start.

---

### Post by James78 on 2010-10-27
Find NameVirtualHost, then add another entry, e.g. 192.168.1.135:443. Find the Listen directive, then add Listen 443. Find the VHost that takes care of server/~user. Copy it, and change <VitualHost 192.168.1.135:80> to <VitualHost 192.168.1.135:443>, then at the bottom add:

SSLEngine on
SSLCertificateFile /path/to/ssl.cert
SSLCertificateKeyFile /path/to/private.key
SSLCACertificateFile /path/to/CA/certificate/if/this/applies/to/you/ssl.ca-bundle

If you don't have a commercial SSL certificate, you'll have to self sign your own, which will give every person visiting your site an error. Look into CaCert if you want too, as they're 100% free, and are almost built in with most browsers and OSes. (You'll still have to add the root certificates to Firefox however, but work is on its way to get that integrated by default)

Note: This will serve as your default SSL VHost, so serving SSL over another same IP VHost will only yield in the first found 443 VHost being used. This is because the server doesn't know which VHost to use because of how SSL works, so it uses the first one. A new technology called SNI (Server Name Identification) is out though, and it's already built into openSSL and Apache2 for Ubuntu, so multiple same IP: port SSL Vhosts will work if the users browser/program supports it (Firefox does now). Non-SNI browsers/programs of course would yield in the default VHost like normal.

Final config:
```
NameVirtualHost 192.168.1.135:80
NameVirtualHost 192.168.1.135:443

Listen 80
Listen 443

<VirtualHost 192.168.1.135:80>
Whatever content is in here
</VirtualHost>

<VirtualHost 192.168.1.135:443>
Copy of port 80 VirtualHost

SSLEngine on
SSLCertificateFile /path/to/ssl.cert
SSLCertificateKeyFile /path/to/private.key
SSLCACertificateFile /path/to/CA/certificate/if/this/applies/to/you/ssl.ca-bundle
</VirtualHost>
```

If you want to force the users to use SSL, you could use mod_rewrite to rewrite every request on the 80 VHost to the 443 VHost. And you could also use a directive like SSLRequireSSL on the port 80 VHost.

Apache2 SSL documentation
[http://httpd.apache.org/docs/2.2/mod/mod_ssl.html](http://httpd.apache.org/docs/2.2/mod/mod_ssl.html)
Ubuntu Apache2 documentation if it helps you anymore than I did.
[https://help.ubuntu.com/6.06/ubuntu/serverguide/C/httpd.html](https://help.ubuntu.com/6.06/ubuntu/serverguide/C/httpd.html)
And the SSL documentation (above link seems to cover SSL too however)
[https://help.ubuntu.com/community/forum/server/apache2/SSL](https://help.ubuntu.com/community/forum/server/apache2/SSL)

---

