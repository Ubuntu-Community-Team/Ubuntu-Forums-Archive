---
title: "Dovecot's LDA ignores aliases"
date: 2009-10-19
forum: Server Platforms
---

### Post by Musicalgibbon on 2009-10-19
///Update

Okay, I've got it behaving properly now, by ignoring Dovecot's LDA and instead switching Getmail to use Sendmail instead. This seems to be properly referencing the aliases.

Incase anyone else has similar issues, the working Getmail config I have is:

```

[retriever]
type = MultidropPOP3Retriever
server = *mailhostexample.com*
username = *user.name*
password = *password*
envelope_recipient = X-Envelope-To:1

[destination]
type = MDA_external
path = /usr/sbin/sendmail
arguments = ("-t", "%(recipient)")

[options]
delete = true

```


///Original Post

Hi all,

I have a(n almost) working mailserver setup using Postfix, Dovecot, Getmail, MySQL hosting virtual users, and Squirrelmail for client access via IMAP. The setup works (as far as my meagre understanding has it) like so:
Mail is retreived by Getmail from our ISP's Multidrop POP3 server, and passed to Dovecot's LDA (called deliver) which checks the SQL user database and, if the user is known, puts the mail in their Maildir folder. Postfix is, *I belive*, only used to send mail out. 

My issue is, that when Getmail passes to Dovecot's LDA, the LDA runs a check on whether the user is valid, and when it does so does not check the alias table. As such any mail that comes in for an alias address (and there are quite a few) is rejected, and the LDA leaves it on our ISP's mail server. 

Am I missing something in the configuration that would provide the LDA/Getmail combo with the aliases, and as such pick all the mail that we require it to? 

Thanks.

---

