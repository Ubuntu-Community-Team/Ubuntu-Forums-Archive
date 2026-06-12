---
title: "webmail in one place and www in antoher"
date: 2009-08-06
forum: Server Platforms
---

### Post by brunoskrebs on 2009-08-06
Hi there,

newbie question. Anyway, I have a domain that is being used only for e-mail purposes and now I want to use it to serve a website. The problem is, the mail is in one server, hosted by a company, and I want to host the website in another server, in another company, without messing everything. I another words, I would like to keep the e-mail server untouched...

So how do I do that? Do I have to use bind9? Is that the way?

Thanks in advance,
Bruno Krebs

---

### Post by grantemsley on 2009-08-06
You have to setup the DNS records appropriately.  This may or may not involve setting up BIND, depending on how things are now.

Here's a basic guide about DNS: [http://www.google.com/support/a/bin/answer.py?hl=en&answer=48090](http://www.google.com/support/a/bin/answer.py?hl=en&answer=48090)

You can find many more if you search for "DNS primer" or "DNS guide" on google.

You'll want the MX records pointing to the server hosting the email, and A records for domain.com and [www.domain.com](www.domain.com) pointing to the server with the website.

If you actually want *webmail* running on a different machine, the most common way to do that is through IMAP.  Squirrelmail, and many other webmail clients, can connect to a different server for IMAP email.

---

