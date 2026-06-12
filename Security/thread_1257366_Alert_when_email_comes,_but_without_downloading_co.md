---
title: "Alert when email comes, but without downloading contents"
date: 2009-09-03
forum: Security
---

### Post by Ulysses_ on 2009-09-03
1. Is there any open-source software that will tell me when I have a new email but not download the contents?  So I can then go and read the email on the web server (yahoo or hotmail).  2. How secure is web-based email access as provided by yahoo or hotmail?  I want to know how difficult it is to break the encryption used.  3. Is there any email provider that offers stronger encryption for web-based access, or even pop3/smtp access?

---

### Post by phillw on 2009-09-04
> **Ulysses_ said:**
> 1. Is there any open-source software that will tell me when I have a new email but not download the contents?  So I can then go and read the email on the web server (yahoo or hotmail).  2. How secure is web-based email access as provided by yahoo or hotmail?  I want to know how difficult it is to break the encryption used.  3. Is there any email provider that offers stronger encryption for web-based access, or even pop3/smtp access?


Gmail (Googlemail)  allows you to monitor other email accounts, you can have https connection, if you choose & flag (filter) the incoming mails as to their source (eg 'hotmail', 'yahoo', etc.) 

It's got pretty good spam filter (you have to teach it some news-letters, authorisation e-mails etc are NOT spam - but it learns quickly !!)

Hopefully this may do what you want.

Regards,

Phill.

---

### Post by lensman3 on 2009-09-04
biff (has been around for years)

See if there is clone.  It works on the local system.  I'm not sure if it can look at remote mail boxes.

---

### Post by Ulysses_ on 2009-09-04
I already have this functionality (Microsoft Instant Messenger for hotmail, yahoo messenger for yahoo), but do not want to use closed-source software any more.  Also I'm not ready to fully move to linux yet.  Anything open-source for windows?

---

### Post by XCan on 2009-09-04
Gmail will be the answer to parts of your question. They offer free pop3, imap as well as smtp access.

---

### Post by Ulysses_ on 2009-09-04
> **XCan said:**
> Gmail will be the answer to parts of your question. They offer free pop3, imap as well as smtp access.

But that is not any better than what I already have security-wise, is it.  I already have Instant Messenger, it's a little icon in the tray that produces an alert when a new email appears in the hotmail server but the email is not downloaded.

Or does gmail come with a notifier that is OPEN-SOURCE and therefore more trusted?  I was looking for an open-source alternative, should have put this in capitals from the beginning. 

Or does gmail have a web interface with stronger encryption than the web interface of hotmail?

---

### Post by Dr Small on 2009-09-04
gnubiff

---

### Post by Mister.Vash on 2009-09-05
This would probably do what you are looking for.

[http://www.nongnu.org/mailnotify/](http://www.nongnu.org/mailnotify/)

---

### Post by Ulysses_ on 2009-09-05
It's just occurred to me that the notifier has to send the password to the mail server, and maybe along the way the password can be stolen, by someone listening who can break the standard encryption.  So something more than standard encryption is required.  Otherwise there is no benefit security-wise in going from IM to any other notifier.

---

