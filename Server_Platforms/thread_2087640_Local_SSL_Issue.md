---
title: "Local SSL Issue"
date: 2012-11-24
forum: Server Platforms
---

### Post by Master_Ne0 on 2012-11-24
Asked [this]("http://askubuntu.com/questions/221013/error-107-neterr-ssl-protocol-error-ssl-protocol-error-on-localhost") over at [askubuntu]("http://askubuntu.com/") and it hasn't got any attention.

I run a website on a cloud server and it uses SSL, I set it up fine [with these instructions]("https://help.ubuntu.com/12.04/serverguide/httpd.html#https-configuration") and issuers instructions.

Though now I need a development environment to test updates, I tried setting up SSL locally using a [self signed certificate]("https://help.ubuntu.com/12.04/serverguide/certificates-and-security.html#generating-a-csr"). 

Though I get an error when I use it.

Error 107 (net::ERR_SSL_PROTOCOL_ERROR): SSL protocol error.

Anyone know what i may have set up wrong?

More info:

I have run through the tests suggested by [This post]("http://support.servertastic.com/error-code-ssl-error-rx-record-too-long/"), my port is certainly open.

---

