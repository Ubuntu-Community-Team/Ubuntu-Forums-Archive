---
title: "dovecot email read problem."
date: 2010-05-05
forum: Server Platforms
---

### Post by Dalik on 2010-05-05
I have 10.04, running postfix and dovecot (default install)
I configured postfix which is accepting emails fine and placing it in a /var/spool/mail in maildir format.

Dovecot also is running and I am able to login with a imap client.
I can send an email to myself just fine but after I send an email to myself the email does not get listed in my inbox.  I check the server and I get this error.  

missing +r perm

Whats happening is the emails are moving from postfix into the dovecot /var/mail/%d/%n location just fine and the permission is vmail:vmail rw--------.

When I login via imap client and login as say userA, dovecot assume permissions for userA and I get this error.  I can chmod 777 on the new emails in /cur and I am able to get a list of emails in my inbox.

How can I have dovecot use user vmail when accessing emails?

I am using virtual users and virtual mailboxes and authentication for system users.

If I can force this one user this would work just fine.

Summary..

dovecot moves email from postfix to dovecot using vmail user.
dovecot access emails as who logged into via imap.
Cant read emails as user who logged in does not have read rights to those emails.

Thank you

---

