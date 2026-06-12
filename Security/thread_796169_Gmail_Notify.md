---
title: "Gmail Notify"
date: 2008-05-16
forum: Security
---

### Post by Zer0Nin3r on 2008-05-16
How safe are the programs [Mail Notification]("http://www.nongnu.org/mailnotify/"), [Gmail Notify]("http://gmail-notify.sourceforge.net/"), and [Check Gmail]("http://checkgmail.sourceforge.net/")?

I looked at the code to Gmail Notify and it seems legit.  Mail Notification I didn't know where to start looking.  I'm just curious how my sensitive information is handled and if it's safe in trasmission between the program and the gmail server; whether or not my information is being sent out to a 3rd party without me knowing it.  Also, are passwords stored encrypted?

Those I listed seem to be the top three programs in the Add/Remove database.

---

### Post by nhandler on 2008-05-17
I haven't actually looked through the source code like you did. Ubuntu has a community of thousands of people. A good percent of those people are developers. I'm sure that many of those people have looked through the source code (either as a learning experience or to check for malicious code). Also, the fact that the package is in the repositories should provide some comfort. It is checked over before being added to make sure it does what it says.

I'm also not sure if they store the information encrypted. However, the fact that the password is stored locally should provide some comfort. You could probably modify the permissions so that only you and the mail notifier could read the file. For example, have the mail notifier be added to a special "mail-notifier" group. Also add yourself to that group. Now, set yourself as the owner of the password file, and set "mail-notifier" as the group. Change the permissions so that the owner and group can both read and write to the file, and so that others can't do anything with the file (chmod 660). This should keep out the other users on your computer.

I'm sorry I couldn't give you straight answers to your questions, but I hope this post will help you anyway.

---

### Post by Zer0Nin3r on 2008-05-17
I like the ideas that you present about creating a separate group access for the program itself.  It never dawned on me to do that.

While I see your points in your post, it makes sense on what you say and yes that does bring about a certain level of comfort.  I will keep your suggestions in mind for future reference.

---

