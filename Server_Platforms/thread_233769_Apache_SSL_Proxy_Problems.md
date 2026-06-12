---
title: "Apache SSL Proxy Problems"
date: 2006-08-10
forum: Server Platforms
---

### Post by Kosh on 2006-08-10
I'm having some trouble getting apache to work as an SSL proxy.  I've seen several similar questions asked on various mailing lists but usually they remain unanswered.

Here's my configuration:
```
<VirtualHost *:443>
  LogLevel debug
  ServerName ssltest.bitstring.org
  SSLProxyEngine On

  ProxyPass / https://ssltest
  ProxyPassReverse / https://ssltest
</VirtualHost>
``` 
HTTP proxies work fine, and I can reach the server internally.  Also the logs show that something is being sent.  The significant portions of the error log file are:

```
Connection: Client IP: 10.0.0.8, Protocol: TLSv1, Cipher: DHE-RSA-AES256-SHA (256/256 bits)
...
/build/buildd/apache2-2.0.55/build-tree/apache2/modules/proxy/proxy_http.c(1514): proxy: start body send
<some "BIO dump follows" messages>
/build/buildd/apache2-2.0.55/build-tree/apache2/modules/proxy/proxy_http.c(1574): proxy: end body send
``` 
On the browser side it says that the connection was terminated.  The Client IP noted is the address of 'ssltest'.  The server has no copy of the SSL certificate, but from my understanding of the docs forwarding traffic to an SSL server does not require any SSL processing on the proxy server.

I would like to know what is wrong with my setup, or find some better documentation about ssl proxies.

Thanks

---

