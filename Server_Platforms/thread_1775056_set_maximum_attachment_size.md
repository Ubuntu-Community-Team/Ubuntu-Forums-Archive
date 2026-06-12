---
title: "set maximum attachment size"
date: 2011-06-04
forum: Server Platforms
---

### Post by hirohitosan on 2011-06-04
Hi there. I use U-server. I set up an mail server as described in Ubuntu Documentation > Ubuntu 11.04 > Ubuntu Server Guide > Email Services.

How can I turn off maximum attachment size. On my server I don't want to limit the size of e mails that arrives.

Thanks a lot

PS
I manage my server with webmin

---

### Post by lfacchinelli on 2011-06-04
are you using postfix or exim4 ??
If you're using postfix in /etc/postfix/main.cf search for [COLOR=#000000][B]message_size_limit [B]directive, or if isn't there, just add it like this

[/B][/B][/COLOR][COLOR=#000000]**message_size_limit = 20480000**[/COLOR] (20mb in bytes)

That number is the max limit size of a message (message itself + attachments)

---

### Post by hirohitosan on 2011-06-05
> **lfacchinelli said:**
> are you using postfix or exim4 ??
If you're using postfix in /etc/postfix/main.cf search for [COLOR=#000000][B]message_size_limit [B]directive, or if isn't there, just add it like this

[/B][/B][/COLOR][COLOR=#000000]**message_size_limit = 20480000**[/COLOR] (20mb in bytes)

That number is the max limit size of a message (message itself + attachments)

Thanks lfacchinelli. It works. :)
[SOLVED]

---

### Post by dodo_ur on 2011-12-20
thank you resolved

---

