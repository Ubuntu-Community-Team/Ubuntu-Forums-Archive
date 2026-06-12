---
title: "My Ubuntu Server 9.04 is freezing"
date: 2010-02-06
forum: Server Platforms
---

### Post by anubis3000bc on 2010-02-06
I have a IBM server x226 series and Ubuntu server works when it's not in the xwindows mode i can run it all day in recovery mode in the shell but when i exit into x window, i then log into ubuntu server and then it freezes after a couple of seconds. Please help asap i really want to get this server up and running smoothly.

---

### Post by volkswagner on 2010-02-07
Your log files should have some helpful info.  If you can ssh into the box run the following:

```
tail -f /var/log/messages
```

With the above open, replicate the action that causes the problem.  The above log should show some relevant info.

Good luck.

---

### Post by Adina on 2010-02-07
I have experienced similar problem in the past. It could be bad ram or graphic card. Maybe use memtest to check ram or change graphic card to see if the problem goes away.

---

### Post by anubis3000bc on 2010-02-07
Well the GPU is onboard so i'll run memtest to check the ram.

---

