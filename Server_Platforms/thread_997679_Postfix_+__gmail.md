---
title: "Postfix +  gmail"
date: 2008-11-30
forum: Server Platforms
---

### Post by notsomeone on 2008-11-30
Anybody know how to connect to smtp.gmail.com with multiple email accounts? I have two domains with Google Apps, and I want my web server to be able to send mail from either one, but the smtp server is the same, so I can't list two accounts in the sasl_passwd file. Postfix complains about duplicate entries even though it's like:
smtp.gmail.com:587  [email]oneguy@thisplace.com[/email]
smtp.gmail.com:587  [email]someone@example.com[/email]

I found this setting "smtp_sender_dependent_authentication" while I was reading the documentation, and I think that could work, but I can't figure it out. I've been at this for three hours and that's enough for one night.

---

### Post by notsomeone on 2008-11-30
I got this working, kind of. I found the answer at the bottom of this page: postfix.org/SOHO_README.html.

The only problem is I want to send emails from web forms, and specify which account to use. But the user is always www-data@<localdomain>. That's the "sender" that Postfix looks at before deciding where to send the email. Don't know if I can do anything about that.

---

### Post by kevdog on 2008-12-01
Do you have a guide how to setup postfix with gmail?  I'd like to use postfix as mail relay to gmail for an smtp server.  Thanks.

---

### Post by notsomeone on 2008-12-02
I think this one was the most helpful:

[http://souptonuts.sourceforge.net/postfix_tutorial.html](http://souptonuts.sourceforge.net/postfix_tutorial.html)

I set it up months ago, and I might have used some other pages too, because it took me a few days to figure out. I didn't bookmark any of them though. I had to search Google to find that link. Hope it helps.

---

