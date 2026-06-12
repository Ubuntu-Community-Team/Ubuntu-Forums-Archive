---
title: "Postfix virtual MAILBOX: separate domains, non-UNIX accounts"
date: 2006-04-27
forum: Server Platforms
---

### Post by luiska on 2006-04-27
Hi

I set up a email server for my domains. Working well, added spamassassin and clamav. Now my next question is:

How do you forward incoming mail for [email]info@domain.org[/email] to [email]someone@domain.org[/email]?

When you hava a Unix account based system, putting a .forward file in the home/user/maildir does it. Where do you place it now?

Thanks
Louis

---

### Post by Glut on 2006-04-28
Generally aliases are used for this, in /etc/postfix/aliases, what type of database are you using for your users?

---

### Post by luiska on 2006-04-28
Hi

I am not using a database. Using 
virtual_mailbox_maps = hash:/etc/postfix/vmaps

Thx
Louis

---

### Post by luiska on 2006-05-05
Hi

I am good at finding my own solutions :)

Well, the answer was quite simple, add the following line to main.cf:
virtual_alias_maps = hash:/etc/postfix/valias

Add the alias to the valias file:
[email]info@domain1.com[/email] [email]info@domain2.com[/email]

postmap valias

Something like that.

t:Louis

---

