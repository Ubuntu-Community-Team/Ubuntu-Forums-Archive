---
title: "Apache Client Certificates"
date: 2009-07-26
forum: Server Platforms
---

### Post by weather15 on 2009-07-26
Hi, I am using ubuntu 9.04 and I am trying to install apache2 and configure it for client certificates is there any documentation of doing this?

---

### Post by LepeKaname on 2009-07-27
I suggest you first to try a FreeSSL before doing it with a real certificate (as they can't be changed once are setup).

Check these ones:
COMODO:
[http://www.instantssl.com/ssl-certificate-products/free-ssl-certificate.html](http://www.instantssl.com/ssl-certificate-products/free-ssl-certificate.html)
GEOTRUST:
[http://www.rapidssl.com/ssl-certificate-products/free-ssl/freessl.htm](http://www.rapidssl.com/ssl-certificate-products/free-ssl/freessl.htm)

And their HOWTO guides:
COMODO:
[https://support.comodo.com/index.php?_m=knowledgebase&_a=viewarticle&kbarticleid=264](https://support.comodo.com/index.php?_m=knowledgebase&_a=viewarticle&kbarticleid=264)
GEOTRUST:
[https://knowledge.geotrust.com/support/knowledge-base/index?page=content&id=AR876](https://knowledge.geotrust.com/support/knowledge-base/index?page=content&id=AR876)

You can have test the certificate within 10 minutes.

---

### Post by weather15 on 2009-07-27
I have used ssl certs before and I am looking for instructions on how to generate the root CA and then generate the client certificates. My only problem is that firefox don't work with self signed client certificates I have explored startssl.com and am I have a free ssl certificate from them now how can I require a key to be on the clients computer to get access and deny all others?

---

### Post by weather15 on 2009-07-29
Bump

---

### Post by chrisinspace on 2009-07-29
I bought a certificate from DigiCert and followed their instructions.  It worked for me.  Step 1 obviously wouldn't apply to you, but I think the rest of the instructions are pretty generic.  

[http://www.digicert.com/ssl-certificate-installation-apache.htm]("http://www.digicert.com/ssl-certificate-installation-apache.htm")

If StartSSL doesn't work for you, I highly recommend Digicert.  Their certificates are affordable and their customer support is excellent.

---

### Post by weather15 on 2009-07-29
I already know how to get ssl working but what I am trying to do is require a unique certificate on each clients computer and is the key file does not exist on the clients system then they will be denied access.

---

### Post by LepeKaname on 2009-07-29
I'm not sure if this is what you want:

> 
This tutorial will show you how to install your own SSL certificate. Such certificates are widely used for personal identification, for example, for online banking systems. The certificate ensures that the person connection is the one who should only have access to the system. 

The password for the certificate is yet another method for identifying that the certificate owner access it. This ensures that even of someone else has access to your computer and your browser it will be impossible for him/her to use the certificate even though it is installed on it. Any time you connect to the remote system that requires this certificate for identification you will be asked for the very same password.

[http://www.onlinehowto.net/Tutorials/Firefox/Install-SSL-certificate-in-Firefox/784](http://www.onlinehowto.net/Tutorials/Firefox/Install-SSL-certificate-in-Firefox/784)

---

### Post by weather15 on 2009-07-31
Yes, But how do I generate the certificates and configure apache first?

---

### Post by LepeKaname on 2009-07-31
> Yes, But how do I generate the certificates and configure apache first?

The way to setup apache is explained in my first answer in this thread in:
> 
And their HOWTO guides:

---

### Post by weather15 on 2009-07-31
That information is to configure ssl as I have done before but what I want is to require client certificates also know as personal certificates to gain access. This meaning that if a client does not have  a key from me they will be rejected access to the website.

---

### Post by LepeKaname on 2009-07-31
Sorry I haven't done that, but I guess that if you generate your certificate with password, and add that certificate to the client, it will ask for the password as well. I'm almost sure about that... I will try to do it myself. I will come back after that.

---

### Post by shredkingj on 2009-07-31
I would recommend creating a certificate authority with OpenSSL.  Generate certificates for each user you want to access, and import those certificates into their web browsers, as well as your CA certificate.

As far as Apache, the configuration looks very straight-forward.  You would just add something like these three lines to your httpd.conf file:

```

SSLVerifyClient require
SSLVerifyDepth 1
SSLCACertificateFile conf/ssl.crt/ca.crt

```Source:
[http://httpd.apache.org/docs/2.0/ssl/ssl_howto.html#allclients](http://httpd.apache.org/docs/2.0/ssl/ssl_howto.html#allclients)

This would require every client, visiting every part of your website to have a valid certificate.  There are more complex examples in the above link.

---

