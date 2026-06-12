---
title: "2 ProxyPass - blank page for deluge torrent"
date: 2010-11-25
forum: Server Platforms
---

### Post by dudumomo on 2010-11-25
Hi there,
I'm trying to blind deluge torrent to port 80 but as I'm running already a server on this port, I've decided to use the ProxyPass option in a vhost.
As I prefer running through HTTPS, I've used my vhost 443 that I already use for bind AjaxTerm (SSH with a web interface)

But whereas AjaxTerm works, Deluge doesn't...I only get a black page but the tab name is correct (ie, Deluge: Web UI 1.3.1)

Here is my vhost

```
<VirtualHost *:443>
        SSLEngine On
        SSLCertificateFile /etc/ssl/private/localhost.pem

     ProxyRequests Off
        <Proxy *>
                AuthUserFile /srv/ajaxterm/.htpasswd
                AuthName EnterPassword
                AuthType Basic
                require valid-user

                Order Deny,allow
                Allow from all
        </Proxy>
        ProxyPass /ssh/ http://localhost:8022/
        ProxyPassReverse /ssh/ http://localhost:8022/
        ProxyPass /deluge/ http://localhost:8112/
        ProxyPassReverse /deluge/ http://localhost:8112/
</VirtualHost>
```

But if I set ProxyPass for deluge to the root folder ie:
```
ProxyPass / http://localhost:8112/
ProxyPassReverse / http://localhost:8112/
```

It works...but obviously I'm not able to use any other 443 services.

Any idea why ?

Thank you !

---

### Post by dudumomo on 2010-12-08
I still haven't figured out why it doesn't work...
Any idea ?

---

