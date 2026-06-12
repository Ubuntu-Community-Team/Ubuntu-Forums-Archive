---
title: "SSL error with Apache2"
date: 2013-10-21
forum: Security
---

### Post by joelgsf on 2013-10-21
I have generated and installed a self-signed ssl certificate for my Apache-2 server, which serves, together with ZoneMinder, to monitor some security cameras. I am running Uvbuntu 12.04.3 server and all SSL setup was done according to the directions in [https://www.digitalocean.com/community/articles/how-to-create-a-ssl-certificate-on-apache-for-ubuntu-12-04]("https://www.digitalocean.com/community/articles/how-to-create-a-ssl-certificate-on-apache-for-ubuntu-12-04") and [http://www.zoneminder.com/wiki/index.php/Ubuntu_Server_12.04_64-bit_with_Zoneminder_1.25.0_the_easy_way]("http://www.zoneminder.com/wiki/index.php/Ubuntu_Server_12.04_64-bit_with_Zoneminder_1.25.0_the_easy_way"), besides my knowledge about OpenSSL and certificates, but, no matter how I tinker with Apache SSL configuration, all I get when trying to access the server via SSL from a browser is an error message which states:
> Error code: ssl_error_rx_record_too_long

Has anyone a hint of what is going wrong?

My Apache-SSL configuration file is as in the attachment.

---

