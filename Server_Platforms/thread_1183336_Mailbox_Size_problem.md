---
title: "Mailbox Size problem"
date: 2009-06-10
forum: Server Platforms
---

### Post by shoaib on 2009-06-10
I am using ubuntu 8.04 for my mail server and postfix as my email soft. Now I want to set mailbox size differently for individual user. For example, one user needs 100 MB mailbox size in server while another user needs 1 GB mailbox size.
 
So, how can I set the mailbox size individually.
 
For your kind information, now I've already set mailbox size as 100 MB for all users in main.cf file.

---

### Post by mfleonhardt on 2009-06-10
I'm no expert on postfix, but this should work:

1. If you are using mbox format out of /var/mail, set up /var/mail to be on a different partition.

or 

If you are using maildir, set up a new partition and use automounter to mount people's maildir's in their home directories.

2. Use quotas on the new filesystem to manage mailbox sizes.

---

