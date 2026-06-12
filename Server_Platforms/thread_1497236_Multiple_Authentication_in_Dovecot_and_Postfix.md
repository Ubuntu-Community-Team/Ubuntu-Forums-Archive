---
title: "Multiple Authentication in Dovecot and Postfix"
date: 2010-05-30
forum: Server Platforms
---

### Post by vl72 on 2010-05-30
Please. tell me, how to configure Dovecot and Postfix service in Linux Ubuntu 9.04.
I want to send and receive email messages to local users and LDAP users.
Now I can send and receive email only between LDAP users and I can send mail from local users to LDAP users.
When I try to send mail from LDAP user to local one, I receive message from Evolution:
“Error while performing operation.
*RCPT TO <user1@local.net> failed: <user1@local.net>: Recipient address rejected: User unknown in virtual mailbox table”*
What I must write in my  /etc/postfix/main.cf and /etc/dovecot/dovecot.conf?
Can anybody help me?

---

### Post by vl72 on 2010-05-31
Help, please !!!

---

### Post by ruuden on 2010-05-31
I believe you need to create virtual mailboxes for your local users and then maybe set up aliases to the local mailboxes.

---

