---
title: "citadel and sendmail"
date: 2010-03-29
forum: Server Platforms
---

### Post by huggy77 on 2010-03-29
I am new to this so i appolgize in advance...

i have a nice running citadel intalll on my server... It works great for regular imap/smtp email...  When i try and run sendmail i get:
message rejected by spam filter
citmail: error #7 occurred while sending mail.
Please check your Citadel configuration.


the command i am using for sendmail testing is:
sendmail -bv [email]recip@addy.com[/email] < /tmp/text.txt

please advise...

Thanks in advance.

---

### Post by volkswagner on 2010-03-29
I was using Sendmail in web pages prior to installing Citadel.  I made a symlink as in the [instructions here]("http://www.citadel.org/doku.php/faq:installation:does_citadel_have"), so now Citadel does it all.

```
cd /usr/local/citadel 
cd /usr/sbin 
mv sendmail sendmail.OLD 
ln -s /usr/local/citadel/citmail ./sendmail 
```

Just another happy Citadel user!

---

### Post by huggy77 on 2010-04-01
it really is an awesome mail server...  It is so easy to set up...

---

### Post by huggy77 on 2010-04-01
i am getting an error when i try and use sendmamil and citadel.  is this a spamassassin problem?

[B]message rejected by spam filter
citmail: error #7 occurred while sending mail.
Please check your Citadel configuration.[/B]

---

### Post by huggy77 on 2010-04-01
it was spamassassin..

i added: whitelist_from  [email]admin@foo.net[/email] to my spamassassin local.cf

---

### Post by huggy77 on 2010-04-01
testing from the command line is turning [email]admin@foo.com[/email] to just @foo.fom...
it is also not including the contents of the text.txt file...

citmail -f "admin@foo.net" [email]christoph@gfoo.com[/email] < text.txt

---

