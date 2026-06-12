---
title: "How to change/suppress boilerplate login text?"
date: 2006-12-16
forum: Server Platforms
---

### Post by peaceful_dragon on 2006-12-16
Is there a way to change the standard boilerplate login text, or even suppress it entirely?

I am talking about this text:

```
Linux blah.blah.com 2.6.15-23-server #1 SMP Tue May 23 15:10:35 UTC 2006 i686 GNU/Linux

The programs included with the Ubuntu system are free software;
the exact distribution terms for each program are described in the
individual files in /usr/share/doc/*/copyright.

Ubuntu comes with ABSOLUTELY NO WARRANTY, to the extent permitted by
applicable law.
You have new mail.
Last login: Sat Dec 16 18:31:18 2006 from tata.toto.com
```

Any ideas? Thanks in advance!

---

### Post by mlind on 2006-12-16
You probably want to change **/etc/motd** file then  (see man motd)

---

### Post by peaceful_dragon on 2006-12-16
Thank you!

---

### Post by chrisfay on 2006-12-16
Let me take that question a step further...

What if I want a custom message displayed when a user attempts to envoke su or sudo?

---

