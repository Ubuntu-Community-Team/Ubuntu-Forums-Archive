---
title: "SSL for zimbra mail server"
date: 2013-05-10
forum: Server Platforms
---

### Post by nerdtron on 2013-05-10
I'm running a zimbra mail server (it's currently still for evalutaion and testing) and it's running just fine. It can already send and receive email from both internal and external domains like gmail, yahoo, etc.

My problem now is the SSL certificate. Every time I point my browser to [https://mail.mydomain.com](https://mail.mydomain.com) a security error is displayed in Chrome and Firefox, although you can ignore this warning, I want to fix this problem.

Another thing is that, when is type just mail.mydomain.com returns an "Unable to connect" error in Firefox. But typing [https://mail.mydomain.ph](https://mail.mydomain.ph) will take me to the login page of zimbra. Is this because of the SSL certificate or a DNS problem.

I hope you help me out fellow server admins. :D
Thanks!

---

### Post by linuxtechguy on 2013-05-10
Did you buy a ssl certificate yet? Self signed certificates will always have that error.

You should start by reading: [http://wiki.zimbra.com/wiki/5.x_Commercial_Certificates_Guide](http://wiki.zimbra.com/wiki/5.x_Commercial_Certificates_Guide)

Your unable to connect problem is either due to dns or the port you are connecting to is not bound to the interface or is being blocked by the firewall.

---

### Post by sandyd on 2013-05-10
> **nerdtron said:**
> I'm running a zimbra mail server (it's currently still for evalutaion and testing) and it's running just fine. It can already send and receive email from both internal and external domains like gmail, yahoo, etc.

My problem now is the SSL certificate. Every time I point my browser to [https://mail.mydomain.com](https://mail.mydomain.com) a security error is displayed in Chrome and Firefox, although you can ignore this warning, I want to fix this problem.

Another thing is that, when is type just mail.mydomain.com returns an "Unable to connect" error in Firefox. But typing [https://mail.mydomain.ph](https://mail.mydomain.ph) will take me to the login page of zimbra. Is this because of the SSL certificate or a DNS problem.

I hope you help me out fellow server admins. :D
Thanks!

Firstly, you need to get a SSL certificate from a provider such as GoDaddy, NameCheap, /etc /etc. After you do that, follow the steps at [http://wiki.zimbra.com/wiki/Installing_a_GoDaddy_Commercial_Certificate](http://wiki.zimbra.com/wiki/Installing_a_GoDaddy_Commercial_Certificate) to setup the certificate

Zimbra is secure, so non-encrypted communications (http) is disabled by default

---

