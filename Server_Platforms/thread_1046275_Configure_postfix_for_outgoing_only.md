---
title: "Configure postfix for outgoing only"
date: 2009-01-21
forum: Server Platforms
---

### Post by legendxx on 2009-01-21
I have postfix setup and everything is working great except for when I try to send emails to the same domain as I have setup in postfix. I get a bounceback saying that this mailbox does not exist. It doesn't even check the mxrecord, it just assumes that it is the destination.

I've tried a couple different things with dpkg-reconfigure postfix including not entering anything for the destination option but it doesn't seem to affect anything. All I need is an outgoing smtp server for sending emails, not receiving. Any tips?

---

### Post by iQwerty on 2009-01-21
If you only need a server for outgoing mails, you don't need the bulky Postfix.

Go with a simple sendmail client like [msmtp]("http://msmtp.sourceforge.net/index.html"), it's works perfectly and eats less RAM :) It's only a little bit harder to get support since it's less popular, [here's]("http://nanotux.com/blog/the-ultimate-server/4/#l-mail") a good guide about setting it up with Google Apps for domain e-mail though, you can adjust the variables quite easily to your situation.

[http://nanotux.com/blog/the-ultimate-server/4/#l-mail](http://nanotux.com/blog/the-ultimate-server/4/#l-mail)

---

### Post by HermanAB on 2009-01-21
Use nullmailer.  It is as simple as it gets.
[http://untroubled.org/nullmailer/](http://untroubled.org/nullmailer/)

Cheers,

Herman

---

### Post by legendxx on 2009-01-21
Thanks guys,

I went with nullmailer. Worked like a charm.

---

