---
title: "You have new mail"
date: 2009-08-21
forum: Server Platforms
---

### Post by damo12 on 2009-08-21
I administer a server for a small business.  I usually access it through Webmin without a problem.  Today I logged in through Putty to restart Webmin and received a message saying "You have new mail".  The server is only a file server and not a mail server.  How do I read this mail.

Sorry for asking what is most likely a very obvious question.

---

### Post by jay.parnaby on 2009-08-21
It will most likely be a notification message from a process running on the server.

The easiest way to look at the mail file through putty would be to use ```
more /var/mail/<username>
```

---

### Post by AlexDudko on 2009-08-21
Perhaps, this is a system mail, which may report some problem or warning. Look in /var/mail or in user's home directory.

---

### Post by prshah on 2009-08-21
> **damo12 said:**
> received a message saying "You have new mail". How do I read this mail.

In the terminal, type ```
mail
``` then "r" to read, "d" to delete, "n" for next message, and so on.

---

### Post by damo12 on 2009-08-21
Thank you for your help, I'll give it a try and see what the message is.

---

