---
title: "a Couple of questions about setting up a mail server"
date: 2012-05-11
forum: Server Platforms
---

### Post by andrejbs on 2012-05-11
I am looking to set up a mail server with the following capabilities:

It should store all sent mail on the server, be able to send mail from a registered email addresses at a domain such as [email]peter@xpublishers.com[/email] to non-local users. Then it should periodically retrieve mails from individual user's mailboxes online, or do so at request from a user and store those mails on the server and serve the mails to users when requested.

The whole purpose is to keep central storage of all mail sent out and received. Bear in mind this should be a non-local mail server.

I had a look at setting up postfix and dovecot ect. but are all of this possible with that?

Some insight would be appreciated.

Thanks,

---

### Post by maverickaddicted on 2012-05-16
Have you seen this -

[https://help.ubuntu.com/community/Squirrelmail](https://help.ubuntu.com/community/Squirrelmail)

---

### Post by SeijiSensei on 2012-05-16
If you need to retrieve mail from external accounts, you'll need to run **fetchmail** as well.

---

