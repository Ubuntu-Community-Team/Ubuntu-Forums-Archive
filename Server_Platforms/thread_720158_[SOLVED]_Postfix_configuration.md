---
title: "[SOLVED] Postfix configuration"
date: 2008-03-10
forum: Server Platforms
---

### Post by neverett on 2008-03-10
I'm working on installing postfix on my system. I followed the directions on [http://www.howtoforge.net/perfect_server_ubuntu7.10_p5](http://www.howtoforge.net/perfect_server_ubuntu7.10_p5) and my main.cf, master.cf and saslauthd files are identical to those listed on the site. I have read about installing postfix on ubuntu in the ubuntu documentation.

When I ```
telnet localhost 25
``` the header comes up normally. I then enter ```
ehlo localhost
``` and everything works without any errors. However, I am missing the following line ```
250-AUTH PLAIN LOGIN
```.

Any ideas on what I am possibly doing wrong? It would be greatly appreciated.

---

### Post by azadpanchi on 2008-03-10
Aside from the fact the line does not appear for you, are you having any other issues?

Do you want postfix configured so even when connecting to it as localhost you have to authenticate?

If postfix is configured to allow locally to send mail without authentication you should be able to send mail using no authentication:
[http://www.astahost.com/info.php/sending-mail-via-telnet_t3325.html](http://www.astahost.com/info.php/sending-mail-via-telnet_t3325.html)

Otherwise after you say helo and enter you will need to type 'auth login' so you can authenticate, you can look to this article for encoding decoding and sending mail using SMTP authentication:
[http://www.webpan.com/customers/Email/SMTP_Authentication_Telnet_Test.htm](http://www.webpan.com/customers/Email/SMTP_Authentication_Telnet_Test.htm)

So to be clear the question you should be concenerd with is if you want postfix to ask for authentication while sending mail locally or not.  If I have miss understood this issue to update clarifying the issue.

---

