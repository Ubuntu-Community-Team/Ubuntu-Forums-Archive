---
title: "how do emails work if you get a new website? (can you use the gmail interface?)"
date: 2012-04-23
forum: The Cafe
---

### Post by hanzj on 2012-04-23
Hello,
Ken is planning on getting a new website registered. Foo.com. The domain registration company said that they could offer Ken one free email address (whatever@foo.com). They said the hosting company Ken chooses could possibly offer him more (unlimited). 

Now Ken loves gmail. Is it possible to use the gmail interface for his foo.com email addresses (ken@foo.cocm, [email]contactus@foo.com[/email]) WITHOUT having the recipients know his real gmail address (kensmith@gmail.com), even if those recipients were to peek at the email headers?

If Ken can use the gmail interface for his  foo.com email addresses, will this be free or will Google charge for this?

---

### Post by mips on 2012-04-23
Yes you can and users will see the [email]ken@foo.com[/email] address. [http://www.google.com/apps/intl/en/group/index.html](http://www.google.com/apps/intl/en/group/index.html)

[http://smarterware.org/3628/host-your-domain-email-at-gmail-without-forwarding](http://smarterware.org/3628/host-your-domain-email-at-gmail-without-forwarding)
[http://danielmiessler.com/blog/how-to-migrate-your-custom-domains-email-to-google-and-maintain-your-addresses](http://danielmiessler.com/blog/how-to-migrate-your-custom-domains-email-to-google-and-maintain-your-addresses)

---

### Post by samalex on 2012-04-23
If you, erm Ken, has access to the DNS for the domain name, he can create an account through apps.google.com then point the MX record on the domain to Google for it to handle the email.  The interface will be the exact same as it is through Gmail.com, but it'll be for foo.com... and he can setup [email]ken@foo.com[/email], [email]kensmith@foo.com[/email], or whatever.  Plus foo.com can take advantage of Google Docs, Google Plus, and most of the other resources Google Apps has.  It's free up to 10 users.

This is what I do on all my domains... works great!

---

### Post by sandyd on 2012-04-23
If you have a vps, run something like iredmail

---

