---
title: "Error while installing Apache2 SSL certificate"
date: 2014-05-13
forum: Server Platforms
---

### Post by shadin2 on 2014-05-13
i wanted install Apache2 SSL certificate on two Ubuntu servers, so I ordered an official verified SSL certificate for both of them then followed these instructions [http://www.digicert.com/ssl-certificate-installation-ubuntu-server-with-apache2.htm](http://www.digicert.com/ssl-certificate-installation-ubuntu-server-with-apache2.htm) to install it.


What i did:
1.change **/etc/apache2** permissions to 777 (i know it's a bad move but i lost the default permissions)
2. copy Intermediate (DigiCertCA.crt) and Primary Certificate (your_domain_name.crt) files to /etc/apache2/ssl directory that i created.
3. copy the key file generated when i created the CSR on the first server to to /etc/apache2/ssl directory.
4. In** /etc/apache2/sites-enabled/** there is one file [000-default] with block **<VirtualHost *:443>**, i kept it and created another file called [secure-deafult] contains:
```


<VirtualHost *:443>
DocumentRoot /var/www/
SSLEngine on
SSLCertificateFile /etc/apache2/ss/my_domain_name.crt
SSLCertificateKeyFile /etc/apache2/ss/my_private.key
SSLCertificateChainFile /etc/apache2/ss/DigiCertCA.crt
</VirtualHost>



```
5. in the **/etc/apache2/sites-available** i changed **VirtualHost _default_:443** to **VirtualHost *:443**


6. restarted apache


then i goth this error in logs:
```
[error] Unable to configure RSA server private key 
[error] SSL Library Error: 185073780 error:0B080074:x509 certificate routines:X509_check_private_key:key values mismatch  

```
any idea?

---

### Post by kosmokramer314 on 2014-05-13
I don't think you have your chain cert setup correctly...checkout this guide. I'm using a chain cert using the steps outlined the link:

[http://arstechnica.com/information-technology/2014/03/taking-e-mail-back-part-2-arming-your-server-with-postfix-dovecot/]("http://arstechnica.com/information-technology/2014/03/taking-e-mail-back-part-2-arming-your-server-with-postfix-dovecot/")

---

### Post by shadin2 on 2014-05-13
> **kosmokramer314 said:**
> I don't think you have your chain cert setup correctly...checkout this guide. I'm using a chain cert using the steps outlined the link:

[http://arstechnica.com/information-technology/2014/03/taking-e-mail-back-part-2-arming-your-server-with-postfix-dovecot/](http://arstechnica.com/information-technology/2014/03/taking-e-mail-back-part-2-arming-your-server-with-postfix-dovecot/)


but i used the file that i received as a cert.

---

### Post by kosmokramer314 on 2014-05-13
> **shadin2 said:**
> but i used the file that i received as a cert.

you also said it wasn't working.

you can look here as well: [http://httpd.apache.org/docs/2.0/ssl/ssl_faq.html#verify](http://httpd.apache.org/docs/2.0/ssl/ssl_faq.html#verify)

---

