---
title: "UEC Store - Certificate verification failed"
date: 2010-07-06
forum: Server Platforms
---

### Post by Sn00kumS on 2010-07-06
Hi, I just installed a little cloud to test some services.
1 CC and 2 NC's.
Now I want to download Images from the Store but I only get:

Error 60: server certificate verification failed. CAfile: /etc/ssl/certs/ca-certificates.crt CRLfile: none

I do not really understand what it wants :)
As I said it's just a test-cloud and hasn't got a domainname yet so I'm just using the IP:8443 and so on.

Someone got an idea what to do?
Oh and I used the CDInstaller all the way.

regards Sn00kumS

---

### Post by sinakoca on 2011-12-07
The issue is discussed on [http://open.eucalyptus.com/forum/server-certificate-verification-failed-0](http://open.eucalyptus.com/forum/server-certificate-verification-failed-0) and these steps solve it :

WARNING: the change disables certificate validation. Use at your own risk!!

Until PycURL is fixed you can edit file /usr/lib/python2.7/dist-packages/imagestore/lib/fetch.py
on fetch method after the line 142
add

curl.setopt(pycurl.SSL_VERIFYPEER, 0)
curl.setopt(pycurl.SSL_VERIFYHOST, 0)

Restart the image-store-proxy

---

