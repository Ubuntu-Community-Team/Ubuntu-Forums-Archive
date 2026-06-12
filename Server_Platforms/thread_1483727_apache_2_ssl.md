---
title: "apache 2 ssl"
date: 2010-05-14
forum: Server Platforms
---

### Post by kpholmes on 2010-05-14
so i follow this guide: [http://beginlinux.com/blog/2009/01/ssl-on-ubuntu-810-apache2/](http://beginlinux.com/blog/2009/01/ssl-on-ubuntu-810-apache2/)

when i go to the site all i get is http, and if i type in the "s" then it cant find the page. its ubuntu desktop 10.04 if that makes a difference, the guide was made from 8.10 but i figured it wouldnt be a problem idk, i use guides written for older version of linux all the time ](*,)

well if anyone can help it would be greatly appreciated

EDIT: ok i found a new tutorial, one thats hopefully updated
[http://www.zimbio.com/Linux/articles/UXP0ymrxfUI/Apache+SSL+Certificate+Authority+CA+Howto](http://www.zimbio.com/Linux/articles/UXP0ymrxfUI/Apache+SSL+Certificate+Authority+CA+Howto)

ill try this out and see how it works.

---

### Post by gangsterkb on 2010-05-15
Hi,

Do you have :

SSLEngine on
SSLOptions +FakeBasicAuth +ExportCertData +StrictRequire
SSLCertificateFile /etc/ssl/certs/server.crt
SSLCertificateKeyFile /etc/ssl/private/server.key

and

sudo a2ensite default-ssl

and

sudo /etc/init.d/apache2 restart

Have you make these changes?  Are you not forgetting some what?
I use the exact same tutorial for setting up SSL all the time.

And it workd allways

Gangsterkb

---

