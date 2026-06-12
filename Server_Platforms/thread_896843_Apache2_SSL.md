---
title: "Apache2 SSL"
date: 2008-08-21
forum: Server Platforms
---

### Post by zdunham on 2008-08-21
Hi, right now I'm running an Apache2 server on the newest Ubuntu, Subversion is running through Apache2. I had SSL running with my own certificate I created using this site: [http://alephzarro.com/blog/2007/01/07/installation-of-subversion-on-ubuntu-with-apache-ssl-and-basicauth/](http://alephzarro.com/blog/2007/01/07/installation-of-subversion-on-ubuntu-with-apache-ssl-and-basicauth/)

My boss just gave me an official company certificate to put in there instead and here were the instructions that came with that:

[http://www.digicert.com/ssl-certificate-installation-apache.htm](http://www.digicert.com/ssl-certificate-installation-apache.htm)

If I take out the lines that I wrote using the first example and put in the ones from the second example the server just fails to load.

The virtual host code is located in the file I created in the first example still, I just inserted the new SSL stuff and removed the old. Any ideas? thanks for any help in advance.

---

### Post by cdenley on 2008-08-21
Any error messages?
```

tail /var/log/apache2/error.log

```
Are you sure it's not waiting for you to enter a password?

---

### Post by zdunham on 2008-08-21
I'll check, give me a minute.

---

### Post by zdunham on 2008-08-21
"Unable to configure RSA server private key"

and also had something else about a key mismatch.

About to leave work in a few minutes so whatever you can leave my I'll reply to tomorrow, thanks for your time.

---

### Post by zdunham on 2008-08-22
I looked up the error on the internet and it says I need to create an RSA key for this specific certificate. We got this special certificate off the internet so how do I create a key to go with a certificate that is already created? if indeed that is the case? And what does CSR stand for? Sorry I'm new to this.

---

### Post by cdenley on 2008-08-22
> **zdunham said:**
> I looked up the error on the internet and it says I need to create an RSA key for this specific certificate. We got this special certificate off the internet so how do I create a key to go with a certificate that is already created? if indeed that is the case? And what does CSR stand for? Sorry I'm new to this.

> 
SSLCertificateKeyFile  should be the key file generated when you created the CSR.

The CSR is a "certificate signature request". It is what you would have sent to the certificate authority before they issued your signed certificate. The RSA key should have been created along with the CSR.

---

### Post by zdunham on 2008-08-22
> **cdenley said:**
> The CSR is a "certificate signature request". It is what you would have sent to the certificate authority before they issued your signed certificate. The RSA key should have been created along with the CSR.

Alright, I should probably have to snag that from my boss then because it was not given to me. Thanks. I'll post back if and when it works thanks for your help.

---

### Post by zdunham on 2008-08-22
Well my boss says I shouldn't need the key, something to do with a wildcard, but the install instructions from the site he got the certificate generated from say to use they key. Who do you think is right?

Also, I have no idea what a wildcard is relating to this or how it would work.

---

### Post by MJN on 2008-08-22
What he might have meant was that the private key has been combined with the certificate. Of course, if he did then he shouldn't have mentioned the word 'wildcard' so perhaps he's actually talking out of his **** (don't tell him that though ;)).

You can check by looking in your certificate - if it is just the signed cert it'll only have a BEGIN CERTIFICATE section, if both it'll also have a BEGIN RSA PRIVATE KEY section too.

Apache needs both - whether that be from one file (referenced by the SSLCertificateFile directive) or separate (referenced by SSLCerficateFile *and* SSLCertificateKeyFile).

Mathew

---

### Post by zdunham on 2008-08-22
> **MJN said:**
> What he might have meant was that the private key has been combined with the certificate. Of course, if he did then he shouldn't have mentioned the word 'wildcard' so perhaps he's actually talking out of his **** (don't tell him that though ;)).

You can check by looking in your certificate - if it is just the signed cert it'll only have a BEGIN CERTIFICATE section, if both it'll also have a BEGIN RSA PRIVATE KEY section too.

Apache needs both - whether that be from one file (referenced by the SSLCertificateFile directive) or separate (referenced by SSLCerficateFile *and* SSLCertificateKeyFile).

Mathew


Thanks for the help, none of the files he gave me have a "BEGIN RSA PRIVATE KEY" section, they all have BEGIN CERTIFICATE sections. When I asked for the key a few minutes ago he gave me a text file containing the certificate request, which I'm guessing the key is used to create, but not the key itself. I'm just an intern and new to this so apparently he thinks its me and passed the job onto another guy...who will probably come ask for the key.

---

### Post by Dr Small on 2008-08-22
Have you read this?
[https://help.ubuntu.com/community/forum/server/apache2/SSL](https://help.ubuntu.com/community/forum/server/apache2/SSL)

---

### Post by zdunham on 2008-08-22
> **Dr Small said:**
> Have you read this?
[https://help.ubuntu.com/community/forum/server/apache2/SSL](https://help.ubuntu.com/community/forum/server/apache2/SSL)


I have thanks, I used that to create the first certificate I used and that worked fine, now they gave me the official company certificate that was made through DigiCert and I don't have the original key that was used to make the certificate request to DigiCert. At least I think that is what's going on.

---

