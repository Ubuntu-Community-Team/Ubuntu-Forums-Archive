---
title: "help installing StartSSL certificate on my server"
date: 2008-05-25
forum: Server Platforms
---

### Post by kustomjs on 2008-05-25
Hey Guys
I need some help on installing StartSSL certificate on to my server but everytime I try to upload the private key on Webmin it gives me this error.Failed to save new key : Missing or invalid PEM format key and certificate what is causing this error?

---

### Post by cviniciusm on 2008-05-25
Hello,

If you're using Ubuntu Server 8.04 LTS then this section of the Server Guide can help you: file:///usr/share/ubuntu-serverguide/html/C/httpd.html

Using apt-get you can install the Server Guide or you can use one at Ubuntu's site.

I think you need a certificate (*.crt) and the private key (*.key).


Regards,
cviniciusm.

---

