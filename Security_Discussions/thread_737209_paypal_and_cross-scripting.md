---
title: "paypal and cross-scripting"
date: 2008-03-27
forum: Security Discussions
---

### Post by KIAaze on 2008-03-27
I have rencently tried to buy something from linuxisos.de.
However, once I reached the paypal site, I got a message from noscript warning me about an XSS cross-scripting attempt.

I now tried out a few other sites using paypal and noticed that all of them seem to use XSS to go to their corresponding paypal page. (otherwise, I stay on the paypal homepage)
The only site I found that didn't cause a warning was sourceforge.net. :confused:

If I set up noscript to allow scripts from any of these pages, I don't get the warning message on paypal anymore.

Is the cross-scripting necessary for sites using paypal?
If yes, how can I know if it's safe? Is there a way to intercept the XSS script and look at it?

Is it safe as long as there is no script being used after hitting the "review order and continue" button on paypal?

---

### Post by The Tronyx on 2008-03-27
I am very rarely the "post a link and forget it," but this should answer all of your XSS questions and concerns.

[http://www.acunetix.com/websitesecurity/cross-site-scripting.htm](http://www.acunetix.com/websitesecurity/cross-site-scripting.htm)

Hope that helps

---

### Post by KIAaze on 2008-03-28
Well, it doesn't answer my main concern yet:
Do commercial websites need to cross-script to paypal?
If they do, is there a way for me to see what script they are injecting?
Or can I at least be sure that it only sends info to paypal, but doesn't retrieve any info from it?

I tried installing the Acunetix Web Vulnerability Scanner with wine (they only offered a Windows version), but it failed with some error about an XML sttings file and "the installation is corrupted" message.

---

### Post by The Tronyx on 2008-03-28
> **KIAaze said:**
> Well, it doesn't answer my main concern yet:
Do commercial websites need to cross-script to paypal?


"Today, websites rely heavily on complex web applications to deliver different output or content to a wide variety of users according to set preferences and specific needs. This arms organizations with the ability to provide better value to their customers and prospects."

You can use Paros Proxy if you want to grab everything that is transmitted in HTTP requests.  It also supports HTTPS and is pretty easy to setup.  It might not be the exact info you are looking for but if you submit dummy information and watch the requests and where it goes, you should be able to see who gets what.

---

