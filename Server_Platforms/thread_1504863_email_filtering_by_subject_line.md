---
title: "email filtering by subject line?"
date: 2010-06-08
forum: Server Platforms
---

### Post by superradical on 2010-06-08
Hi, I was wondering how to set up a simple rule on the server side so emails with a certain subject just go into that user's .Trash.  
Right now my users will get roughly 25,000 of the same email from our corporate offices and it is destroying their email clients.
I believe the mail setup is postfix and courier with virtual users.
I tried googling this up but I couldn't find much current or ubuntu-specific information.

---

### Post by Bachstelze on 2010-06-08
You can use procmail, with a rule like:

```
:0:
* ^Subject: <your subject here>
$HOME/.Trash/

```

The path might need to be adjusted.

*Yay, 8,000!*

---

### Post by superradical on 2010-06-08
I'm not sure if this will work as we are running virtual mailboxes.

---

### Post by noway2 on 2010-06-09
CMUSieve should be able to do it.  [http://wiki.dovecot.org/LDA/Sieve](http://wiki.dovecot.org/LDA/Sieve)

If I recall correctly, you install it and add a small script to your pop/imap serve configuration.

It uses regular expression pattern matching to write rules and then take appropriate action.  I used to use it on my mail server to handle the spam.  I didn't have it setup right and was too new to understand it and decided to delete it, so I can't give you a lot of help on how to use it, but I am sure it will do the trick for you.

---

