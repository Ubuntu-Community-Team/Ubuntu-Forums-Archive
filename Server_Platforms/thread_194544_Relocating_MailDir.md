---
title: "Relocating MailDir"
date: 2006-06-11
forum: Server Platforms
---

### Post by neillans on 2006-06-11
Hi all,

First off - configuration:

Exim4 (Heavy)
Courier IMAP

Running on Dapper Drake

I am currently saving mail to $HOME/Maildir (default), however, I'd like to relocate all users Maildirs to another drive (actually, in this case its a LVM volume - /data/web/mail/mailboxes/).  I'd like to be able to seperate them out the same as the standard home directory - e.g /data/web/mail/mailboxes/andy/.

Some of you will wonder why I just don't move the home directories - I have a number of users that store a lot of data on the system, and I would like to seperate mail (already moved www data) for all users into a central LVM so that its easier to backup, manage etc.

I know I can change the Maildir for Courier in imapd, however, it does not seem to have any means to set it to an absolute path with a user variable.

Anyone have any ideas how I can achieve this?

Andy

---

