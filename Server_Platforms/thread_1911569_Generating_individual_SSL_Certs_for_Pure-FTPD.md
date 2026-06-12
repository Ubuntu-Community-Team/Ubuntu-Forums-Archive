---
title: "Generating individual SSL Certs for Pure-FTPD"
date: 2012-01-19
forum: Server Platforms
---

### Post by kembar4 on 2012-01-19
Hey guys,

I plan to setup a FTP server and instead of blocking user access, I want to do it the easier way, where I enable TLS and these users would be given a certificate that would expire after 30 days.

This is the command that I use to generate the cert:

```
 sudo openssl req -x509 -nodes -newkey rsa:1024 -days 30 -subj "/C=RANDOM/ST=RANDOM/L=RANDOM/O=RANDOM/CN=www.mywebsite.com" -keyout /etc/ssl/private/pure-ftpd.pem -out /etc/ssl/private/pure-ftpd.pem 
```

Once that command runs, a cert is generated successfully. I tried logging into the server from Filezilla (WINDOWS) and the server wouldn't accept the plaintext connection. Changed Filezilla's encryption to login using Explict FTP over TLS and I am asked to accept the certificate that would last for 30 days. 

I believe this one certificate works for every user that I created / will create. How do i change it so that every client would be given an individual certificate. (That way, an account created 2 weeks later, will have 30 days until expiry, or some accounts would have 90 days until expiry).

Is this do-able?

---

