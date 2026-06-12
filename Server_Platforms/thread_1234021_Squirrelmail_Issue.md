---
title: "Squirrelmail Issue"
date: 2009-08-07
forum: Server Platforms
---

### Post by kmowery on 2009-08-07
I have built a mail server on Ubuntu 8.04LTS using Postfix and Dovcot.  I am able to pass mail and recieve mail; however, when logging in with Squirrelmail no mail shows in my in box?  I can see mail when looking at mailboxes with webmin but not squirrelmail.  I have setup my mailbox with Maildir nor mbox.  Can someone point me to the bad configuration statement (I'm guessing)?

---

### Post by noway2 on 2009-08-07
Can you access your mail with a regular IMAP program like Evolution or Outlook?

---

### Post by kmowery on 2009-08-07
Actually no - I had not tried until you asked.

---

### Post by kmowery on 2009-08-07
I resolved my issue all is well.  I removed dovcot and went with courier and all worked just as expected!  I love linux!

---

