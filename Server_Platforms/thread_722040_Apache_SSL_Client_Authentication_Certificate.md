---
title: "Apache SSL Client Authentication Certificate"
date: 2008-03-12
forum: Server Platforms
---

### Post by asforme on 2008-03-12
After many hours of googling and reading half a dozen how-to's I finally got SSL working in apache in Ubuntu 7.10 Gutsy.  Success finally came after finding this how-to ([https://help.ubuntu.com/community/forum/server/apache2/SSL#head-6097389ac6c921feb19fca8ddbc03278cb115738](https://help.ubuntu.com/community/forum/server/apache2/SSL#head-6097389ac6c921feb19fca8ddbc03278cb115738)) and following the instructions for Gutsy.

Now I want to take this a bit further.  My website will be served over the internet, but not publicly.  I will be only serving it to trusted friends and family.  Therefor I would like to have authentication via client certificates.  According to this apache documentation ([http://httpd.apache.org/docs/2.0/ssl/ssl_howto.html#allclients](http://httpd.apache.org/docs/2.0/ssl/ssl_howto.html#allclients))  it should be fairly easy to implement but I really don't know where to start.

The guide for setting up SSL in apache that I followed had me use ```
sudo make-ssl-cert /usr/share/ssl-cert/ssleay.cnf /etc/apache2/ssl/apache.pem
```  I ran that command and it automagically made a key file for me, but I have no idea where the Certificate Authority is or how I can create a client certificate that will properly authenticate.

---

### Post by asforme on 2008-03-12
Anyone?

---

### Post by asforme on 2008-03-14
bump

---

### Post by Naoi on 2008-03-16
I just started researching this same idea myself and I found a few links which may be helpful to you.

For this link:

[**Creating a self-signed SSL certificate: Ubuntu**]("http://http://www.tc.umn.edu/~brams006/selfsign_ubuntu.html")

look towards the end of the page there's a section called "Generating a CA under Ubuntu" that talks about making a Certificate Authority and then refers to this [ **link** ]("http://www.tc.umn.edu/~brams006/selfsign.html") for most of the steps.

I also found another how-to that doesn't specifically use Ubuntu but describes a similar  process [**here**]("http://www.vanemery.com/Linux/Apache/apache-SSL.html"), it also talks about making certificates for clients.

Please bear in mind I am just starting out learning  about this subject and haven't actually tried these guides yet, but they seemed promising and I hope they are helpful to you. :)

---

