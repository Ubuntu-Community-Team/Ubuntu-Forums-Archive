---
title: "[SOLVED] HTTPS Self Signed Cert help"
date: 2008-01-21
forum: Server Platforms
---

### Post by Scot1967 on 2008-01-21
I have gone through the following doc...

[https://help.ubuntu.com/6.06/ubuntu/serverguide/C/httpd.html](https://help.ubuntu.com/6.06/ubuntu/serverguide/C/httpd.html)

and setup my new Ubuntu Apache web server with a self signed cert for HTTPS.  The server answers on 443 OK and the site is displayed however IE says there is a problem with the cert.  So obviously I thought to import the cert file into IE.  This did not help.

Any advice on how to troubleshoot what I may have done wrong?

Thanks.

---

### Post by Scot1967 on 2008-01-21
I re-did my ssl files and used the full site name for the CN (common name) and it seems to be working now.  

Used [www.mycompany.com](www.mycompany.com) for CN instead of just mycompany

   openssl req -new -key server.key -out server.csr

I then re-created the self signed cert...

openssl x509 -req -days 365 -in server.csr -signkey server.key -out server.crt

copied it to where it needed to go....

sudo cp server.crt /etc/ssl/certs
sudo cp server.key /etc/ssl/private

Imported it into my web browser...

Tada!  no more error message in IE.

---

