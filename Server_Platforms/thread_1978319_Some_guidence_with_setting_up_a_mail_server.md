---
title: "Some guidence with setting up a mail server"
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

### Post by SeijiSensei on 2012-05-11
You'd only need to add [fetchmail]("https://help.ubuntu.com/community/GmailPostfixFetchmail") to that configuration.  That's a utility to download messages from a remote server and deliver them locally.

---

