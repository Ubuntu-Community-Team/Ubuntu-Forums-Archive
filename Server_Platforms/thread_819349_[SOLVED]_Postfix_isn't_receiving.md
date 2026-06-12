---
title: "[SOLVED] Postfix isn't receiving"
date: 2008-06-05
forum: Server Platforms
---

### Post by Dr Small on 2008-06-05
I booted the server after a bad thunderstorm and noticed I was not receiving any mail. I can send mail fine and receive it on the other end, but I can not receive mail.

nmap tells me that port 25 is open, postfix is running. Where else do I look? So far, I have not received a delivery failure at the other email account, so I don't have any errors to play with yet.

Dr Small

---

### Post by Dr Small on 2008-06-05
I solved it.
When I was trying to fix mailman the other day, I ran a few commands that adds options to postfix's main.cf file. Well it added the first one on the end of a line, which messed up the configuriation for it.

Now I just need to get mailman fixed :D

---

