---
title: "Imap"
date: 2007-01-27
forum: Server Platforms
---

### Post by soon82 on 2007-01-27
I have install xmail (pop3&smtp) on my ubuntu box. it is running very well. Currently i would like to install courier imap for my mail server. How to intergrated xmail with courier imap server. 

Thank you

---

### Post by kidders on 2007-01-28
Hi there,

Unless you're doing something odd with your mail management, xmail and courier shouldn't really need to be aware of eachother.

I don't have any experience with xmail, but I'm assuming it puts incoming mail in a sensible place (maybe users' home directories), and stores it in a standard format, (such as maildirs or mboxes). If that's true, you *should* simply be able to point courier to the same location, without any problems.

---

