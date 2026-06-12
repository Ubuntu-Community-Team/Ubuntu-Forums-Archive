---
title: "Email Aliases"
date: 2008-01-26
forum: Server Platforms
---

### Post by DavidRussellCA on 2008-01-26
I'm looking for an easy way to set up an email redirect.  I've got a server and it's running Courier/Postfix and Mailman to run a mailing list.  I'd like to be able to create a quick [email]username@server.server.ca[/email] thing that will direct the mail onto a Gmail or other account.

Is this easy?  I've never had any luck with setting it up.

---

### Post by HermanAB on 2008-01-26
Nullmailer?

---

### Post by DavidRussellCA on 2008-01-27
Won't that ruin Mailman?

I've added

user:    [email]user@gmail.com[/email]

to the aliases file and run newaliases and it sometimes works - but for instance I can't send email from the gmail account to the address that directs back to the gmail address.

---

### Post by MJN on 2008-01-27
What happens when you do? Some sort of loop-detection going on?

Mathew

---

