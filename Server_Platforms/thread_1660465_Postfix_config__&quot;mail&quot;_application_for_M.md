---
title: "Postfix config / &quot;mail&quot; application for Maildir directories"
date: 2011-01-05
forum: Server Platforms
---

### Post by jstalin on 2011-01-05
I set up postfix on my server, according to the instructions here:

[https://help.ubuntu.com/community/PostfixBasicSetupHowto](https://help.ubuntu.com/community/PostfixBasicSetupHowto)

The problem is that after setting up Maildir style mailboxes in postfix, the "mail" application no longer works, since it is looking for mail in /var/mail/username. There are no instructions for making "mail" work after the switch to Maildir mailboxes. The instructions above seem to be lacking.

Anyone have any ideas how to use "mail" or any other mail application to access the mail in /home/username/Maildir?

---

