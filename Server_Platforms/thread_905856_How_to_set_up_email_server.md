---
title: "How to set up email server?"
date: 2008-08-30
forum: Server Platforms
---

### Post by serverCrazy on 2008-08-30
i would like to set it up my email server as following:

POP3 - pop3.mydomain.com
IMAP - imap.mydomain.com
SMTP - smtp.mydomain.com


any ideas, how it can be done. Do i have to create a subdomain on my domain name provider? or what........................?


thanks in advance.

---

### Post by gishaust on 2008-08-30
I have been just putting an email server together myself and pop3, smtp, and imap are only transport vehicles for an email server. If you are looking to sent up an email server I used postfix, but there is exim, sendmail and others.I used dovecot as the pop3 and imap as a transport server. smtp comes with postfix

---

### Post by starcannon on 2008-08-30
Heres a very well written guide on the subject.
[http://flurdy.com/docs/postfix/](http://flurdy.com/docs/postfix/)

GL and Have fun.

---

### Post by windependence on 2008-08-31
Yes, you will need to properly set up your domain with the proper MX records. It's also important with a mail server to properly set up reverse DNS so you don't get blacklisted. After your server is set up, check to make sure you don't have an open relay by using a site like [http://www.abuse.net/relay.html](http://www.abuse.net/relay.html).

You can do what you want and maybe you just want to learn to set up a mail server, but if you just want to get one up as fast as possible with little headache, then you could go with a bundled package like Zimbra, or Citadel. Exim is easy to set up and available as a package from the Ubuntu repos.

-Tim

---

### Post by HermanAB on 2008-08-31
Here you go:
[http://www.citadel.org/doku.php?id=installation:start](http://www.citadel.org/doku.php?id=installation:start)

---

