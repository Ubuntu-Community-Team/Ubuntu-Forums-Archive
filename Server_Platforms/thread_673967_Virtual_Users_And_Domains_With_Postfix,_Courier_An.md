---
title: "Virtual Users And Domains With Postfix, Courier And MySQL"
date: 2008-01-21
forum: Server Platforms
---

### Post by root_at_home on 2008-01-21
Hi there

I followed the following link setting up postfix...

[http://www.howtoforge.com/virtual-users-and-domains-with-postfix-ubuntu-7.10-p4](http://www.howtoforge.com/virtual-users-and-domains-with-postfix-ubuntu-7.10-p4)

In there I installed amavisd-new, SpamAssassin, And ClamAV, Is there a way to get a control panel to administrat this?

Please let me know.

Many Thanks

Root_at_home

---

### Post by HermanAB on 2008-01-21
Yesss... sorta, with a lot of effort.  You need Webmin and Virtualmin.  Google for it.  Setting it up is however a lot of work.  Another problem with this is that only the user data is in a database.  The messages are still in mbox or maildir storage.  So if you send a message to multiple users, then multiple copies are stored eating up disk space.

If you don't want to waste time and have a better system with a database backend that only stores a single copy of any message, then you need Citadel: [http://www.citadel.org](http://www.citadel.org)

Cheers,

Herman

---

### Post by root_at_home on 2008-01-21
thanks for the reply will look into it.

:-)

---

### Post by gnaunited on 2008-01-21
I just set that up for Debian Etch. It would be perfect if it had a control panel, but I am comfortable using phpMyAdmin to set it all up.

---

