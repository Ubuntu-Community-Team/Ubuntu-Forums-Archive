---
title: "Use of Citrix &amp; certificates in Firefox"
date: 2008-11-21
forum: Security
---

### Post by d98rolb on 2008-11-21
I ant to connect to my work. We use a weblogin with certificates and then Citrix. I have downloaded and installed a Linux ICA client from [http://www.citrix.com/English/ss/downloads/details.asp?downloadId=3323&productId=186&c1=sot2755#top](http://www.citrix.com/English/ss/downloads/details.asp?downloadId=3323&productId=186&c1=sot2755#top)
I use a 64-bit Ubuntu 8.10.

Then I imported my personal certificate and my works server certificate.
The installation went well and I restarted firefox.

But when I try to start an citrix application at work I got this dialog
(translated from Swedish):

This place require you to identify yourself with a certificate:
Issued by ""

I choose my personal certificate and press ok.
Then another dialog appear:

You have choosen to not trust "Ahola Transport". The issuer of the servers certificate (SSL error 61).

What can I do ?

---

### Post by lemming465 on 2008-11-22
If firefox is the application with the issue, you need to edit the trust settings on the imported certificate.  Go into Edit -> Preferences, Advanced tab, View Certificates button.  Find your problematic certificate, highlight it, and use the Edit button dialog to turn on the missing trusts.

---

