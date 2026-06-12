---
title: "courier server with alias domain"
date: 2011-05-09
forum: Server Platforms
---

### Post by pbrille on 2011-05-09
Hi,
I set up a mailserver using this tutorial:
[https://help.ubuntu.com/community/MailServerCourierSpamAssassin](https://help.ubuntu.com/community/MailServerCourierSpamAssassin)

It works fine so far.
I run this server for a small company with about 20 mailboxes where a address looks like that.

[email]user@domain.com[/email]

Now I want to set up an alias domain so that 
[email]user@domain2.com[/email] also automatically is directed into the mailbox of "user".

Can someone give me a hint please. THX
Pbrille

---

### Post by pbrille on 2011-05-15
Found it out by myself.

When there's a user called "user" and there are more than one domains declared for which courier accepts incoming Emails, then automatically all emails to [email]user@domain1.tld[/email] and also [email]user@domain2.tld[/email] will be dropped into the mailbox of "user"...

---

