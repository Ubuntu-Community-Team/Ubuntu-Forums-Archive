---
title: "Procmail"
date: 2009-07-12
forum: Server Platforms
---

### Post by Mailme on 2009-07-12
Procmail question

Why doesn't this work?

MYEMAIL=joe@example.com

:0
* ^To: $MYEMAIL
{

do some action

}

I send the email to [email]joe@example.com[/email] & it always fails !!!!

Driving me up the wall!!!!!

---

### Post by HermanAB on 2009-07-12
```
:0:
* ^To:.*joe@example.com
```

---

### Post by Mailme on 2009-07-12
Thank you for this, but what I was after was setting a VARIABLE wich I can put at the start of my script & not need to type out the email each and every time.

---

### Post by HermanAB on 2009-07-12
Procmail is very primitive.  Use Search and Replace in an editor.

---

### Post by Mailme on 2009-07-13
Many thanks for your help.

---

