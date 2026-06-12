---
title: "Mailserver for testing purpose"
date: 2009-09-10
forum: Server Platforms
---

### Post by ericchaves on 2009-09-10
Hi Folks,

I'm trying to build a mailserver to test an notification software. I'm trying postfix + davencot but since i'm not familiar with them I'm having a hard time to configure it.

What I'd like to do is setup the server so that any messages that it receives, no matter which domain it belongs, should be either delivered to the local virtual user, otherwise it should be delivered to a special "catch-all" mailbox.

The desired behavior would be:
 1-No messages should ever be delivered outside of the server *ever*. its a server for local testing only.
 2-Messages to local virtual domains should be delivered to the correct user (this is working already since its default behavior of postfix+davencot:)).
 3-Any other messages should be delivered to a specific user's mailbox.
 4-No messages should bounce ever.
 5-The sever should not query DN for MX records, since not all message domains would be valid.
 6-All mailboxes, including the "catch-all" one, should be acessible by IMPAP and SMTP.

Could anyone help me out on this task?

Thanks in advance.

Eric.

---

