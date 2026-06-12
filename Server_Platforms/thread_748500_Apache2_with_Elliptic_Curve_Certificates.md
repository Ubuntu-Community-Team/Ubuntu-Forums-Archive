---
title: "Apache2 with Elliptic Curve Certificates"
date: 2008-04-07
forum: Server Platforms
---

### Post by webhog on 2008-04-07
I managed to get Apache configured and working properly with normal RSA certificates, now that I know I have the Apache configuration right, I want to run it with ECC certificates.  I have not been able to get it working... I don't know if it is because I'm not generating the certificates properly, or if there are additional configuration parameters that I have to add for ECC certificates.
When I create a certificate with the following commands, my browser tells me I am using unrecognized encryption.  I am certain it can handle the ECC certificate I am trying to generate, because I have accessed ECC test websites which run the same type of certificate I am trying to generate. 

To generate the certificates, I have followed these steps with OpenSSL (I created a CA beforehand, with a regular RSA certificate):

openssl ecparam -out server2.pem -name sect571r1 -genkey

openssl ec -in server2.pem -out server2.key

openssl req -new -key server2.pem -out server2.pem

openssl x509 -req -in server2.csr -out server2.crt -sha1 -CA ca.crt -CAkey ca.key -CAcreateserial -days 365



My apache configuration is very simple(this is for a small vpn network):

listen 10.8.0.1:8080
listen 10.8.0.1:443
<VirtualHost 10.8.0.1:443>
ServerName 10.8.0.1
SSLEngine On
SSLCertificateFile /etc/apache2/ssl/server2.crt
SSLCertificateKeyFile /etc/apache2/ssl/server2.key
SSLCertificateChainFile /etc/apache2/ssl/ca.crt
SSLCACertificateFile /etc/apache2/ssl/ca.crt
SSLCipherSuite ECDHE-RSA-AES256-SHA
DocumentRoot /var/www/apache2-default/
</VirtualHost>


Am I generating the ECC keys correctly?  Does the CA certificate have to be an ECC certificate too?  Any other suggestions?  
Thank you

---

### Post by palban on 2008-05-04
hi i have same problem. I generate ECC kay and certificate with this key, but when i start apache it not work :(

---

