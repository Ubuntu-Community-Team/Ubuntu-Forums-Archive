---
title: "[SOLVED] ircd-hybrid"
date: 2008-11-13
forum: Server Platforms
---

### Post by kennedy7 on 2008-11-13
OK, i installed ircd-hybrid and it worked fine untill reboot. I had followed a howto on sourcefourge. People were able to connect to it and everything but i rebooted. Now when i try to start ircd-hybrid with this
command "invoke-rc.d ircd-hybrid start" it gives me this sad news
"Starting Hybrid 7 IRC Server: ircd-hybridinvoke-rc.d: initscript ircd-hybrid, action "start" failed." what would be doing this.
Im am running ircd-hybrid, Ubuntu-8.10.
Any help would be greatly welcome!

---

### Post by CrucifiedEgo on 2008-11-13
Is there anything in /var/log/ that looks interesting?  i'm not sure what file ircd-hybrid logs to, maybe ircd.log -- or check debug/messages for anything interesting after the failed startup attempt.

---

### Post by kennedy7 on 2008-11-14
Hmm, ok check out my irc Its gonno work until reboot.
[http://irc.tyspage.doesntexist.com](http://irc.tyspage.doesntexist.com).
Then you can chat with me and see that its ok until i reboot.
you can either download the program i got or chat directly from my site.
or xchat.

---

### Post by kennedy7 on 2008-11-14
> **CrucifiedEgo said:**
> Is there anything in /var/log/ that looks interesting?  i'm not sure what file ircd-hybrid logs to, maybe ircd.log -- or check debug/messages for anything interesting after the failed startup attempt.

And unfortunatly i turned off logging to save boot time.

---

### Post by kennedy7 on 2009-08-31
I have solved my problem. Apperently i couldnt seem to grasp the fast you need to read the manual pages before you go configuring

---

