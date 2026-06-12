---
title: "Help - Postfix not delivering to maildir ?"
date: 2013-11-25
forum: Server Platforms
---

### Post by MrEgg on 2013-11-25
Since our lastest Ubuntu 10.04.4 updates, strange behavior is happening to our Postfix/Roundcube server.

Postfix can send and receive emails, as we can see them come and go in the queue.

When connecting to the email account via roundcube, Postfix removes the message from the queue. However, we do not see the message arrive as a new message in Roundcube. It is nowhere to be found.

This is a server I am taking over from someone who had configured it last year, without leaving any notes, so I have to look at every possible way one after the other. Yet, I don't understand why the messages seem to get lost.

Please help :(

---

### Post by clearski on 2013-11-25
Do you have this line in your main.cf?

```
home_mailbox = Maildir/
```

---

### Post by MrEgg on 2013-11-27
Solved.

It was actually a problem with mailproc, which was not delivering to the proper folders. It must have been part of the updates and its config file must have be modified for some reason. Analyzing /var/log/mailproc.log helped solve the issue.

---

