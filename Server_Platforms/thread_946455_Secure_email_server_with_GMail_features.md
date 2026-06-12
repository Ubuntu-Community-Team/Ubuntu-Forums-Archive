---
title: "Secure email server with GMail features"
date: 2008-10-13
forum: Server Platforms
---

### Post by dignus on 2008-10-13
Hey all,

I've been asked to build a super-secure e-mail server setup. The basics are pretty easy, encryption etc. 

Now for the MTA + MUA part: $company is currently using Google Apps for Domains. They absolutely *LOVE* the GMail webmail client and would like to see a three of it's features in the new setup:
 - threading
 - labels
 - Ajax interface (don't get me started...)

A webmail client is a must-have, POP3/IMAP is optional if the webmail client is that good. 

Anyone who can recommend a decent webmail client that offers these functions? I've seen Squirrelmail, has threading, but the 1994 design lacks the Ajax thingy these guys are looking for.
Payware is not a problem, if it offers the right features and if it can be installed on a local box, not hosted.

Thanks!

---

### Post by cdenley on 2008-10-13
The best webmail client I have ever used is zimbra. I never used gmail, though. It supports threading, has a very nice AJAX interface which looks like a web application. Even the non-javascript version has an application look and feel. I'm not sure what you meant by "labels".
[http://www.zimbra.com/products/hosted_demo.php](http://www.zimbra.com/products/hosted_demo.php)
I don't think there is any way to integrate the zimbra interface into an already running mail server, though. Is the IMAP/SMTP already done?

---

### Post by dignus on 2008-10-13
> **cdenley said:**
> The best webmail client I have ever used is zimbra. I never used gmail, though. It supports threading, has a very nice AJAX interface which looks like a web application. Even the non-javascript version has an application look and feel. I'm not sure what you meant by "labels".
[http://www.zimbra.com/products/hosted_demo.php](http://www.zimbra.com/products/hosted_demo.php)
I don't think there is any way to integrate the zimbra interface into an already running mail server, though. Is the IMAP/SMTP already done?

Thanks for the reply! I'll definitely take a look at Zimbra. IMAP/SMTP has not been finished yet, I'm only designing this thing on paper at the moment. FYI: labels in GMail are tags in Zimbra, looks good. Again: thanks!

---

### Post by cdenley on 2008-10-13
> **dignus said:**
> Thanks for the reply! I'll definitely take a look at Zimbra. IMAP/SMTP has not been finished yet, I'm only designing this thing on paper at the moment. FYI: labels in GMail are tags in Zimbra, looks good. Again: thanks!

The reason I asked was because Zimbra is an all-in-one solution. Should make your design a bit simpler.

---

### Post by Robstarusa on 2008-10-13
I can vouch for zimbra.

It is an exchange killer!

---

### Post by dignus on 2008-10-13
> **cdenley said:**
> The reason I asked was because Zimbra is an all-in-one solution. Should make your design a bit simpler.

Yeah, I see that. Thanks!

---

