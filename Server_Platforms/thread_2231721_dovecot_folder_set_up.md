---
title: "dovecot folder set up"
date: 2014-06-27
forum: Server Platforms
---

### Post by shad2 on 2014-06-27
if i have this path to my users' emails:
home_mailbox = Maildir/
in postfix,And in dovecot i heve mail_location: maildir:/home/bal/vmail/%d/%n/Maildir as the folder for my mails
how can I set up dovecot to create the folders trash,spam,drafts automatically?????

---

### Post by SeijiSensei on 2014-06-28
You can edit the directory /etc/skel to build a template for new user accounts.  I use mbox format rather than Maildir and created an /etc/skel/mail directory with the appropriate folders. Since all the files in /etc/skel are hidden by default, you'll need to use "ls -la" to see what is in that directory. Perhaps you can modify my method to work with Maildir. 

Frankly for small mail servers with a few users, mbox is much easier to manage.  Just give each user a Unix account with /usr/sbin/nologin as her shell.

---

### Post by thnewguy on 2014-06-28
Dovecot automatically makes those folders for you, there isn't any need to change the Dovecot configuration. Once you specify MailDir at the mail_location, Dovecot handles the creation of those folders.

---

