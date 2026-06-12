---
title: "Ubuntu One on Lubuntu behind a proxy"
date: 2012-06-21
forum: Ubuntu One (CLOSED)
---

### Post by alanrburns on 2012-06-21
Hi 
I am trying to get Ubuntu One working behind a proxy
Lubuntu 12.04
Ubuntu One client 3.0.1

I have installed the Ubuntu One client Proxy support and did the following 

u1sdtool -q
export https_proxy=http://username:password@host:port/
u1sdtool --start

error message: 
Unhandled error in Deferred:
Unhandled Error
Traceback (most recent call last):
Failure: ubuntu_sso.utils.webclient.common.WebClientError: (u'Connection refused', u'')


I would think there is a proxy property in ~/.config/ubuntuone/syncdaemon.conf but it doesn't seem like it..


Is there any devs that know I can insert the proxy settings?

---

