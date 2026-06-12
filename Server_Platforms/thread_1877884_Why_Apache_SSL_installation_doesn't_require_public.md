---
title: "Why Apache SSL installation doesn't require public key"
date: 2011-11-08
forum: Server Platforms
---

### Post by trongbang on 2011-11-08
I'm following this tutorial: [http://www.sitepoint.com/securing-apache-2-server-ssl](http://www.sitepoint.com/securing-apache-2-server-ssl) (please go to section "CREATE A LOCAL KEY PAIR")

As you can see, what we need is a certificate and a private key which can be obtained through the following 2 lines:
[LIST]
[*]openssl genrsa -des3 -out domainname.com.key 1024 
[*]openssl req -new -key domainname.com.key -x509 -out sslname.crt
[/LIST]

If you know a bit about public private key infrastructure, you can understand that to read and write messages in an understandable way for both sender and the receiver which are in this case our web browser and the web server, we ought to have a public key and a private key.

So my question is why don't we have to generate a public key for that installation?

---

### Post by hawkmage on 2011-11-08
You do have a private and public key.  The file domainname.com.key is your private key.  Your public key/cert is in the sslname.crt file.

On the openssl req command the -x509 option makes it generate a self signed certificate instead of a Certificate Signing Request.

---

### Post by trongbang on 2011-11-09
> **hawkmage said:**
> You do have a private and public key.  The file domainname.com.key is your private key.  Your public key/cert is in the sslname.crt file.

On the openssl req command the -x509 option makes it generate a self signed certificate instead of a Certificate Signing Request.

Thanks for your quick reply,
Can you please confirm whether you're saying that the public key is the certificate itself?

Thanks in advance,

---

### Post by linuxwin2 on 2011-11-09
To print the content of your certificate do :
```
$ openssl x509 -in sslname.crt -text -noout

```

---

### Post by hawkmage on 2011-11-09
Yes with x509 certificates the public key is the same thing as the certificate.  The only difference between traditional public key and a x509 certificate is that the x509 certificate is digitally signed by its self or a certificate authority.

---

