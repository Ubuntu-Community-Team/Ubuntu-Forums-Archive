---
title: "postfix config'd Maildir, how to pull /var/mail leftovers?"
date: 2008-07-03
forum: Server Platforms
---

### Post by jeffk on 2008-07-03
I just got my preferred postfix+dovecot(-1.1.1) configuration working on Ubuntu 8.04 server. Users and Maildirs migrated, etc.

I wasn't seeing inbound mail (in the email client) until I set:
> sudo postconf -e 'home_mailbox = Maildir/'
Which I hadn't needed in the previous server's main.cf

I have a few hours worth of inbound mostly-spam in /var/mail/(username) during the time I was figuring this out.

What command line tools could I use to pull those message from the mboxes to the Maildirs?

Thanks.

---

### Post by MJN on 2008-07-04
Hi Jeff,

There is a nice tool (Perl script) to do this at [http://batleth.sapienti-sat.org/projects/mb2md/](http://batleth.sapienti-sat.org/projects/mb2md/)

Note the warning about running it as the user of the mailboxes, and not root, or else you'll be scratching your head for hours!

Mathew

---

