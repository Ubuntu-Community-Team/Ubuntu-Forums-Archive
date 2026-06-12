---
title: "Dovecot Maildir++ directory structure"
date: 2009-04-24
forum: Server Platforms
---

### Post by rconen on 2009-04-24
I'm using IMAP with Dovecot with a little problem. Currently have configured Postix and Dovecot to use the Maildir format for storage.

I've noticed in my test invironment that where I use Thunderbird that the . (dot) in a folder name is accepted. Dovecot uses the . for storing subfolders.
This will mess up the directory structure when a folder with a . is created.

What are the solutions to solve this problem. I've checked it also with Microsoft Outlook Express which will notify the user that the . cannot be used.

On this page from the dovecot website: [http://wiki.dovecot.org/MailboxFormat/Maildir](http://wiki.dovecot.org/MailboxFormat/Maildir)
you can read that there is an option to use the standard directory structure of the filesystem.
I'm using Ubuntu Server 8.04 LTS which has Dovecot v1.0.10 while Dovecot v1.1 can use the filesystem directory structure. How can I install this new version on my Ubuntu installation to test the normal directory configuration.

---

### Post by rconen on 2009-04-27
I've solved the problem by upgrading my system to 8.10
Now I have a newer version of Dovecot which supports the filesystem layout of the Maildir.

By chaning the line:
mail_location = maildir:/home/vmail/%d/%n

To:
mail_location = maildir:/home/vmail/%d/%n:LAYOUT=fs

fixed the problem after restarting Dovecot.

---

