---
title: "Prostfix cant send mails"
date: 2010-04-10
forum: Server Platforms
---

### Post by t_ras on 2010-04-10
using kubuntu 9.04 on AMD 64,working with ISPconfig panel.
I have mail configured with Postfix. It works fine from the server (and of course through squirrelmail installed in it), but I cant send from other computers.
Any ideas?

THanks

---

### Post by ruuden on 2010-04-10
After you try to send mail check your mail log with this command:

```
tail -20 /var/log/mail.log
```this command will show the last 20 entries in your mail log

---

### Post by t_ras on 2010-04-10
Thanks for th tip. it seems it was an authentication issue. I tried specific type. when left for Outlook to choose it worked fine.

---

