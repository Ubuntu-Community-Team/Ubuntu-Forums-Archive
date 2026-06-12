---
title: "Thinking of going to Ubuntu"
date: 2006-09-22
forum: Server Platforms
---

### Post by DRicher33 on 2006-09-22
Hi all,

Question for the experts:

I'm currently running MS Small Office Server and I hate it.  However, in order for me to switch over to Ubuntu server I need to satisfy my manager's unique needs.

She wants to be able to get email remotely (mostly from home) and be able to browse through her stored emails.  She need to see perhaps older emails from a year ago.  Currently we use MS Outlook Remote to do this and it works fine.  She can browse through the mail realtime from home and then come into the office to work on Outlook there.

She wants to run the same program at home and at the office (doesn't matter what program as long as it is good).  Does Ubuntu offer a solution similiar to sbs2003?

Any advice would be appreciated!  Help me get off this MS train to nowhere!!

Dave

---

### Post by Child of Wonder on 2006-09-22
Postfix and Courier-IMAP or Dovecot IMAP.

She can configure any client she wants to connect to the server and read her email from anywhere since it's stored on the server.

---

### Post by fstab on 2006-09-23
I agree.  Postfix and Dovecot IMAP worked for me.

---

