---
title: "Apache SSL Configuration Troubleshooting"
date: 2010-07-19
forum: Server Platforms
---

### Post by naifwonder on 2010-07-19
I am trying to configure Apache on my server to work with ssl, but everytime I visit my site, I get the following message in my browser:


[B]SSL connection error.

Unable to make a secure connection to the server. This may be a problem with the server, or it may be requiring a client authentication certificate that you don't have.

Error 107 (net::ERR_SSL_PROTOCOL_ERROR): SSL protocol error.[/B]


Just some background on the situation: I am using Ubuntu 10.04 desktop edition. I installed apache by installing zend server (it installed apache automatically). I then installed openssl. Non-https pages work fine on the site. I tried getting trial certificates from multiple certificate sites but nothing is working (same error). I was previously hosting my site on another server on which ssl worked just fine. I also tried using the key and crt file from that server, but I got the same error. The domain name and IP are still the same though. My SSLCertificateFile and SSLCertificateKeyFile are pointing to the correct directory and files.

If anyone has any suggestions, it would be most appreciated.

---

### Post by timothy_tim on 2010-07-19
Are you using Google Chrome?  This might provide some information [http://www.google.com/support/forum/p/Chrome/thread?tid=6052fff553a29392&hl=en](http://www.google.com/support/forum/p/Chrome/thread?tid=6052fff553a29392&hl=en).

Otherwise you could check if you are accidentally requiring an client certificate.

---

### Post by naifwonder on 2010-07-19
I am using google chrome, but the site is not working on any browser. I do not have SSLVerifyClient enabled so I do not think the server is requiring clients to have anything special.

---

### Post by timothy_tim on 2010-07-26
Have you already checked the logs (e.g. Apache error logs)?

Maybe someone here will spot an error in your configuration, if you posted it here.

---

