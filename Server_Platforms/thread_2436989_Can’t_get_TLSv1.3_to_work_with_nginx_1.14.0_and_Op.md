---
title: "Can’t get TLSv1.3 to work with nginx 1.14.0 and OpenSSL 1.1.1 on Ubuntu 18.04.4"
date: 2020-02-16
forum: Server Platforms
---

### Post by greelan on 2020-02-16
I've posted this question ([https://askubuntu.com/questions/1210619/can-t-get-tlsv1-3-to-work-with-nginx-1-14-0-and-openssl-1-1-1-on-ubuntu-18-04-4](https://askubuntu.com/questions/1210619/can-t-get-tlsv1-3-to-work-with-nginx-1-14-0-and-openssl-1-1-1-on-ubuntu-18-04-4)) over at AskUbuntu, but no replies as yet, so trying my luck here.

Title says it all - I am running Ubuntu Server 18.04.4, with nginx 1.14.0 (built with openssl 1.1.1) and openssl 1.1.1, but can't get TLSv1.3 to work on my nginx server.

I have added reference to the TLSv1.3 protocol and ciphers in my nginx config, but nothing.

Any ideas anyone?

(Sorry for not posting the same details here as I posted in my AskUbuntu question, but everything time I try, I get a "Forbidden" response from the Ubuntu Forums Apache server...)

---

### Post by wildmanne39 on 2020-02-16
Hello and welcome to the forum.

*Thread moved to **Server Platforms a more appropriate sub-forum**.*

---

### Post by mörgæs on 2020-02-18
I shall admit that I have no particular knowledge regarding encryption but in general I don't expect old software like 18.04 to support new protocols as for example TLS 1.3.
Have you tried 19.10?

---

### Post by greelan on 2020-02-18
TLSv1.3 support was backported to 18.04 with the 18.04.3 point release. See the releases notes ([https://wiki.ubuntu.com/BionicBeaver/ReleaseNotes/ChangeSummary/18.04.3](https://wiki.ubuntu.com/BionicBeaver/ReleaseNotes/ChangeSummary/18.04.3)) and associated nginx bug description ([https://bugs.launchpad.net/ubuntu/+source/nginx/+bug/1836366](https://bugs.launchpad.net/ubuntu/+source/nginx/+bug/1836366)).

So, as I said, with the versions of nginx and openssl that I now have, I should be able to enable TLSv1.3.

I only use LTS releases on production servers.

---

### Post by kevdog on 2020-02-18
What kind of SSL certs do you have? RSA or another type?  Where exactly are you getting your config for nginx?  Mozilla generator?

---

### Post by greelan on 2020-02-18
I have both RSA 2048 and ECDSA 384 certs installed, from Let's Encrypt. My cipher settings are indeed based on the Mozilla generator.

---

### Post by kevdog on 2020-02-18
Can you temporarily remove the ECDSA certs?  I've tried those multiple times before, and for whatever reason they always caused errors.

---

### Post by greelan on 2020-02-18
Tried as you suggested, but no change in result unfortunately. The certs seem OK, because they work happily with TLSv1.2.

---

### Post by kevdog on 2020-02-19
I posted over on AskUbuntu since I wasn't able to reply here for some strange reason

---

### Post by kevdog on 2020-02-19
I additionally modified my nginx server to "remove my intermediate config" and use the ssl-params you originally posted:

```

ssl_protocols TLSv1.2 TLSv1.3;
ssl_prefer_server_ciphers on;
ssl_ciphers TLS_CHACHA20_POLY1305_SHA256:TLS_AES_256_GCM_SHA384:TLS_AES_128_GCM_SHA256:ECDHE-ECDSA-AES256-GCM-SHA384:ECDHE-RSA-AES256-GCM-SHA384:ECDHE-ECDSA-CHACHA20-POLY1305:ECDHE-RSA-CHACHA20-POLY1305:ECDHE-ECDSA-AES128-GCM-SHA256:ECDHE-RSA-AES128-GCM-SHA256:DHE-RSA-AES256-GCM-SHA384:DHE-RSA-AES128-GCM-SHA256;
ssl_ecdh_curve X25519:secp384r1;

```

I still didn't have a problem completing the TLS handshake

---

### Post by greelan on 2020-02-21
I've solved my issue. I had a default_server config also included in /etc/nginx/sites-enabled/, which didn't have the TLSv1.3 flag in the ssl_protocols parameter (in fact, it didn't have a ssl_protocols parameter at all). This apparently caused the failure, even though my tests were run on hostnames that were served by different server blocks. Go figure!

---

### Post by kevdog on 2020-02-21
Glad you got it figured out.

---

