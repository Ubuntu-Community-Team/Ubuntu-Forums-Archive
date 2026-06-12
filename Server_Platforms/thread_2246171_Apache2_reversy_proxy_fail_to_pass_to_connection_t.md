---
title: "Apache2 reversy proxy fail to pass to connection to backend with ssl"
date: 2014-09-28
forum: Server Platforms
---

### Post by lesbianpenguin on 2014-09-28
Hi,

im having this problems almost a week now, and i have no idea how to solve this,

i have a apache2 reverse proxy (with ssl) passing the connection to another server running tomcat with ssl. i keep getting this error message on browser

> Proxy Error

The proxy server received an invalid response from an upstream server.
The proxy server could not handle the request GET /.

Reason: Error reading from remote server

on the error logs it says

> [Mon Sep 29 11:29:43.494799 2014] [proxy_http:error] [pid 2221:tid 140582592702208] (103)Software caused connection abort: [client 192.168.12.94:37724] AH01102: error reading status line from remote server xxx.xxx.xxx:443
[Mon Sep 29 11:29:43.494992 2014] [proxy:error] [pid 2221:tid 140582592702208] [client 192.168.12.94:37724] AH00898: Error reading from remote server returned by /

however it works if i passed it through non ssl tomcat.. need help on this matter.. below is the setting for my proxy configuration

```
SSLSessionCache        shmcb:/home/gpki/ssl_scache(512000)
SSLSessionCacheTimeout  300
Servername xxx.xxx.xxx

<VirtualHost *:443>

    SSLEngine On
    SSLProxyEngine On

SSLProxyCheckPeerCN off
SSLProxyCheckPeerExpire off
SSLProxyCheckPeerName off

SSLProxyProtocol all
SSLProxyVerify optional_no_ca

    ProxyRequests Off
    ProxyPreserveHost On

    SSLCertificateFile /etc/apache2/ssl/server.crt
    SSLCertificateKeyFile /etc/apache2/ssl/serverkey.key
    SSLCACertificateFile /etc/apache2/ssl/verisign.crt

#    ProxyHTMLInterp On
#    ProxyHTMLExtended On

    ProxyPass / https://xxx.xxx.xxx/
    ProxyPassReverse / https://xxx.xxx.xxx/

    SetEnv proxy-initial-not-pooled
    SetEnv proxy-nokeepalive 1


</VirtualHost>

```

thanks

---

### Post by lesbianpenguin on 2014-09-29
managed to solve it... need to configure tomcat to allow only sslv3 to make it work

---

