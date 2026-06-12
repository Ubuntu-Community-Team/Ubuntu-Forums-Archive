---
title: "Trigger command when mail arrives"
date: 2009-06-10
forum: Server Platforms
---

### Post by ZarlacMing on 2009-06-10
Hi,

I have some trouble getting started with this. 
I'm using PostFix as a mailserver and when a mail arrives it is saved to the users /home/user/Maildir/new/ directory.

I need a way of sensing when there is a new mail in the mailbox. When an e-mail arrives a script is executed with the file as a parameter. The script must be executed pretty much on the second of arrival.

Any good ideas on how to proceed?

---

### Post by unutbu on 2009-06-10
Take a look at the "incron" package. It gives you the functionality you are looking for. Here is an explanation of how to set it up:
[http://ubuntuforums.org/showpost.php?p=7379763&postcount=3](http://ubuntuforums.org/showpost.php?p=7379763&postcount=3)

Edit: After posting the above message, I'm having some second thoughts. There might be a better -- or at least easier, or prettier way which I don't know about. You might want to wait for other people to respond.

I don't have any experience with any of these packages, but they all claim to be mail notifiers: xmailbox, xlassie, newmail, mail-notification-evolution, mail-notification, kgmailnotifier, kcheckgmail, ixbiff, gnubiff, gmail-notify, coolmail, biff

---

### Post by ZarlacMing on 2009-06-11
Excellent, incron did exactly what I wanted.

Thanks alot for the help!

---

