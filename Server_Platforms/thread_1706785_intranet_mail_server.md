---
title: "intranet mail server"
date: 2011-03-14
forum: Server Platforms
---

### Post by chinna saaeb on 2011-03-14
I want to setup an intranet mail server as a project. I tried to go through various forums but could not get a satisfactory model.
My sceme of things is as follows:
The server a virtual machine is after a router which has a built in dhcp server.
Prefer to use sendmail but postfix ok
client machines should be able to access the mail on evolution/thunderbird or web access using squirrelmail
Can anybody suggest a simple scheme?
Mail will not be relayed to anybody outside the intranet.

---

### Post by Demented ZA on 2011-03-14
A fairly common approach to this would be to use postfix as your MTA, and dovecot as your MDA. Both are fairly simple to set up. Postfix just needs to be set to handle mail for your local domain. Both dovecot and postfix will need to know where your users mailboxes reside (by default /home/user/Maildir for the Maildir type mailbox).

---

