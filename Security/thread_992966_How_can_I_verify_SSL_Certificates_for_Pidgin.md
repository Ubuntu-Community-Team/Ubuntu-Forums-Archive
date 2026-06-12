---
title: "How can I verify SSL Certificates for Pidgin"
date: 2008-11-25
forum: Security
---

### Post by ajacx on 2008-11-25
Earlier today I had to run a bunch of security updates on 8.04LTS and it looks like one of the security updates was for pidgin, and on checking [http://www.ubuntu.com/taxonomy/term/1+2/0](http://www.ubuntu.com/taxonomy/term/1+2/0) I found:

It was discovered that Pidgin did not validate SSL certificates when using a secure connection. If a remote attacker were able to perform a man-in-the-middle attack, this flaw could be exploited to view sensitive information. This update alters Pidgin behaviour by asking users to confirm the validity of a certificate upon initial login. (CVE-2008-3532)

So when I started Pidgin today I get this message: "Accept certificate for nexus.passport.com?
The root certificate this one claims to be issued by is unknown to Pidgin."

with the three options to accept, reject or view certificate.

Can someone please tell me how I can verify that the certificate Fingerprint (SHA1) is authentic for the different IM service providers?

Thanks!

---

### Post by cdenley on 2008-11-25
Open it in firefox.
[https://nexus.passport.com/](https://nexus.passport.com/)
You'll get the message "The page is unavailable or no longer exists". If you don't get a big warning from firefox about the SSL certificate, then firefox was probably given the correct certificate verified by a trusted certificate authority. To get the SHA1 fingerprint, click on the lock icon in the bottom right, then click "View Certificate".

---

### Post by almahtar on 2008-11-25
1.  Point firefox to [https://nexus.passport.com](https://nexus.passport.com)
2.  Double click the padlock icon in the status bar at the bottom of firefox
3.  Make sure it says it's verified by Verisign.  Click "View Certificate".
4.  When the Certificate's info pops up, verify that the SHA-1 field on that dialog matches the one in Pidgin.  It's ok if one's upper case and the other's lower case as long as the letters and numbers match.


Screenshot, in case I worded things in a confusing way:
[http://znatd.com/verify.jpg](http://znatd.com/verify.jpg)

---

### Post by rungss on 2008-12-08
What if they do not match????


Common name: gmail.com

=============================================
Pidgin
=============================================
Fingerprint (SHA1): 9f:f8:3b:da:2c:a3:12:55:24:d5:b9:d6:fc:49:69:8f:0a:91:d8:cd

Activation date: Wed Apr 11 22:47:38 2007

Expiration date: Tue Apr 10 22:47:38 2012

---

