---
title: "local mail in mailq does not get delivered"
date: 2007-10-29
forum: Server Platforms
---

### Post by honigbluete on 2007-10-29
I just installed Ubuntu 7.10 Server with all servers besides a DNS on an offline machine. It shall stay offline until everything is configured. Then I did a sudo dpkg-reconfigure postfix to "Internet site". Afterwards I set up some user accounts and aliases to /etc/aliases. Now I want to test local mail. I wrote some testmails for various users. mailq shows them but they do not get delivered. No files for those users have been created under /var/spool/mail. What might be the reason for this that the mails do not get delivered?

---

### Post by MJN on 2007-10-29
Post your config (/etc/postfix/main.cf) and mail log (/var/log/mail.log) and we can take a look.

Mathew

---

### Post by honigbluete on 2007-10-30
I got it. I failed to fill useful content into the file /etc/postfix/sender_canonical, to build the database out of it and restart the server. Works now :-) Thanks for pointing me to the right files.

---

