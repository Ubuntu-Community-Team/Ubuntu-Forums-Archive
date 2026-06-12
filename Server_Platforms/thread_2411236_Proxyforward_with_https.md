---
title: "Proxyforward with https"
date: 2019-01-27
forum: Server Platforms
---

### Post by cazz on 2019-01-27
Hi
I have a Ubuntu server 18.04 with apache2 install and everything works fine.

I have work Before with proxyPass but then I did use http.


Now I going to run two site that need to have https so I was trying to make it same but got no luck

I have in my router port foward 443 and I have also try with http>https

The lastest I try now is this



```
<VirtualHost *:80>
    ServerName page.domain.nu
    SSLProxyEngine on
    SSLProxyVerify none
    SSLProxyCheckPeerCN off
    SSLProxyCheckPeerName off
    SSLProxyCheckPeerExpire off
    ProxyPass / https://192.168.1.10/page
    ProxyPassReverse / https://192.168.1.10/page
</VirtualHost>
```

When I run this code it sa to me when I trying to go to [http://page.domain.nu](http://page.domain.nu)

> ERR_TOO_MANY_REDIRECTS

it also give me 

[http://page.domain.nu//](http://page.domain.nu//)

---

