---
title: "openssl Error: Unable to get Local Issuer certificate"
date: 2017-03-29
forum: Security
---

### Post by sriramp on 2017-03-29
All Experts,

I have been struggling for couple of days to establish ssl communication between ubuntu 16 and my windows 2012 server. I have imported a domain certificate (created through CA server which is also windows) to my windows 2012 server > Server Certificates. The same .cer file is copied to my ubuntu 16 /etc/ssl/certs folder. My agent application on Ubuntu 16 should make use of this certificate and send my agent related file via https to my windows 2012 server. While sending the file via https, it throws "OpenSSL Error: Unable to Get Local Issuer Certificate". I did this before in the past and it worked. But, now after following same steps, it does not work. Please guide me. Your help is much appreciated. Throw some SSL light on me about how does it work. I am always confused with SSL.

Thanks in Advance,
Sriram

---

### Post by TheFu on 2017-03-29
All my certs in that directory are in PEM format.  [Google found]("https://serverfault.com/questions/254627/how-to-convert-a-cer-file-in-pem") this answer to convert:

```
$ openssl x509 -inform der -in certificate.cer -out certificate.pem
```

The openssl manpage doesn't mention the -inform der part, so I don't know what that does here.  Lots of "See Also" commands in the manpage.

The link (above) says there is an issue with Windows-generated certs. It provides other commands.

---

### Post by sriramp on 2017-03-30
Thanks TheFu. I tried coverting .cer to .pem using the command you sent. After converting into .pem file, I get the same error in my application log file:

> 
[Thu 30 Mar 2017 09:50:04 AM IST (G, 0)] {2274} Uploading file 'system on ubuntux86srirm at 20170330T095003 (Full).gz' to 'https://administrator@172.26.82.91/RemoteDir/'[Thu 30 Mar 2017 09:50:04 AM IST (N, 0)] {2274} Error 0xE1BBFC14: OpenSSL error 0xFC14: unable to get local issuer certificate
[Thu 30 Mar 2017 09:50:04 AM IST (N, 0)] {2274} Error 0xE050044D: Failed to create remote directory /RemoteDir




---

### Post by TheFu on 2017-03-30
In the link, there are other solutions. Try them?

---

