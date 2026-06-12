---
title: "Relation between user mailbox and normal mailbox"
date: 2010-12-24
forum: Server Platforms
---

### Post by gertjan_schouten on 2010-12-24
Hello,

I am running server Ubuntu with Postfix as mailserver. Postfix uses MySQL to store the domains and the users. The actual emails are stored in the vmail user homedir.

I have a question: Each user that is added in the MySQL database gets his own accout with POP3-Access (through Courier). But each *linux user* on the server also has his own mailbox (in var/mail/username). How do those mailboxes relate? How do you arrange for POP3 access for these linux user mailboxes?

Thanks!

Gert-Jan

---

### Post by Calimo on 2010-12-26
Hi,
> **gertjan_schouten said:**
> But each *linux user* on the server also has his own mailbox (in var/mail/username).Are you sure they're still active?
I guess they were created automatically when you installed postfix, and then they weren't removed when you setup virtual mails. But now if you send an email to a user who doesn't have a virtual account, it should be rejected (and you should check that rather than believing me blindly ;)).

---

### Post by gertjan_schouten on 2010-12-26
Thanks! I'll check it out asap!

---

