---
title: "Dovecot Backup with Dsync"
date: 2014-08-03
forum: Server Platforms
---

### Post by Dominic--- on 2014-08-03
Hello guys.

I have two servers running Dovecat.
Now I want to _backup_ the maildata to the second server.

Both have Dovecot installed.
When I run: dsync -u username backup domain.com I receive these two messages:
dsync-remote(dominic): Error: open(/var/mail/dominic) failed: Permission denied (euid=1000(dominic) egid=1000(dominic) missing +w perm: /var/mail, we're not in group 8(mail), dir owned by 0:8 mode=0775)
dsync-remote(dominic): Error: Can't create mailbox INBOX: Internal error occurred. Refer to server log for more information. [2014-08-03 14:01:35]

Now on my second servers nothing is showing up on the syslog or mail log.

From what I am seeing the folder /var/mail/%u is being is approchaed but my mail is stored in /home/user/Maildir.

Can someone tell me how I can fix this?

---

