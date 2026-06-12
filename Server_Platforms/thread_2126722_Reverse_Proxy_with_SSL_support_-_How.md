---
title: "Reverse Proxy with SSL support - How?"
date: 2013-03-18
forum: Server Platforms
---

### Post by KaMZaTa on 2013-03-18
Hi,

I need to configure a Reverse Proxy to forward connection request to my 3 web server (I have 1 IP only and dynamic). I read good opinion on Squid but problem with SSL support to. I need to rebuild from source with option --enable-SSL? Can you tell me more? There was a guide?

[IMG]http://img812.imageshack.us/img812/5194/servermap.jpg[/IMG]

Thank you

---

### Post by KaMZaTa on 2013-03-18
I build squid with success and with --enable-ssl option.

Now reverse proxy on port 80 work very well but port 443 doesn't work. I create SSL Certificate with no problem. I use this squid.config:

```

http_port 80 accel vhost
https_port 443 accel cert=/usr/newrprgate/CertAuth/testcert.cert key=/usr/newrprgate/CertAuth/testkey.pem

cache_effective_user squid
cache_effective_group squid
cache_peer 192.168.10.52 parent 80 0 no-query originserver login=PASS name=site1-http
cache_peer 192.168.10.52 parent 443 0 no-query originserver login=PASS ssl sslflags=DONT_VERIFY_PEER name=site2-ssl
cache_peer_domain site1-http mysite.com www.mysite.com
cache_peer_domain site2-ssl mysite.com www.mysite.com


```

What's wrong?

---

