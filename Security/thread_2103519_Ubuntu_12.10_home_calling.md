---
title: "Ubuntu 12.10 home calling"
date: 2013-01-10
forum: Security
---

### Post by FiberJoe on 2013-01-10
Hello Ubuntu!

I have totally fallen in love with Ubuntu desktop! Super nice Linux distribution! 

Just wish I could hug it! Erhmz, never mind...

Hi all, I was wondering all those home calling connections I see. Is there any way to disable those?

I was login in on the console by ALT-F2  and saw immediately connections to:
eloko.canonical.com 
kwaimuk.canonical.com

Some process named remote login something was connecting to them. I already tried removing zeitgeist and stuff like that.. (geoip is a biatch, cant remove it without unity)(


How can I permanently stop this home calling behaviour? Which config files do I need to edit?

---

### Post by LuciferRex on 2013-01-10
Maybe try changing reporting settings under All Settings -> Privacy -> Diagnostics tab

---

### Post by mc4man on 2013-01-10
You could remove this package if not using the remote-login & see
remote-login-service
(- in a terminal
```
sudo apt-get purge remote-login-service
```

There are 2 other packages you could look at removing if desired
lightdm-remote-session-freerdp
lightdm-remote-session-uccsconfigure

---

