---
title: "Postfix create maildir"
date: 2014-05-29
forum: Server Platforms
---

### Post by Sky_rider on 2014-05-29
How do you make postfix create maildir folders automatically for all users?


I have these two lines in my postfix main.cf, which supposed do create maildir folder at /home/user after the first mail but it is not working. What am I missing?
> 
home_mailbox = Maildir [FONT=Consolas, Menlo, Monaco, Lucida Console, Liberation Mono, DejaVu Sans Mono, Bitstream Vera Sans Mono, Courier New, monospace, serif]/[/FONT]
mailbox_command = 

At the moment mail looks to sent, but nowhere to be found.

---

### Post by gtozzi on 2014-05-30
For what I can remember, postfix doesn't create it.

You have to create it on /etc/skel and for every old user with maildirmake

---

