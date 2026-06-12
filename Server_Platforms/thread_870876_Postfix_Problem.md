---
title: "Postfix Problem"
date: 2008-07-26
forum: Server Platforms
---

### Post by Black Mage on 2008-07-26
I am having a problem in postfix where I can't send mail. When I issue an ehlo, I get this:

ehlo
501 Syntax: EHLO hostname


Does anyone know what this means?

Thnx

---

### Post by songshu on 2008-07-26
aren't you supposed to tell it whom to say ehlo to by means of the hostname?

like 
ehlo mail.example.com

---

### Post by Black Mage on 2008-07-26
Thanks, dumb dumb mistake. And I got the mail server working too.

---

