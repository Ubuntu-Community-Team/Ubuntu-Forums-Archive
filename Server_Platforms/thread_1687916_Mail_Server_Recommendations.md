---
title: "Mail Server Recommendations?"
date: 2011-02-14
forum: Server Platforms
---

### Post by Zeon100 on 2011-02-14
Hey guys,
I'm looking for a mail server for ubuntu that can do black/whitelisting per user. I was looking at postfix but not sure if that can do this. For example the following:

*@gooddomain.com WHITELIST
[email]spammer@gooddomain.com[/email] BLACKLIST
*@* BLACKLIST

The above would allow anyone from gooddomain.com to send through while [email]spamm@gooddomain.com[/email] and any other sender wouldn't be able to email through. Recommendations appreciated :)

---

### Post by SeijiSensei on 2011-02-15
[MailScanner]("http://www.mailscanner.info/") will let you write all sorts of rules like this.  It will also scan every message with a virus checker like ClamAV and scan for spam with SpamAssassin.

Takes a bit of work to set up, but it's worth it in the long run.

A simpler solution might be to use sendmail with access rules like the ones described [here]("http://www.sendmail.org/m4/anti_spam.html").

---

### Post by James78 on 2011-02-15
You might also try something like [this]("http://www.cyberciti.biz/faq/howto-blacklist-reject-sender-email-address/").

---

