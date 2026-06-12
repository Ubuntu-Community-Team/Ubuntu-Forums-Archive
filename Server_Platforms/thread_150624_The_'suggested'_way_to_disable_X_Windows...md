---
title: "The 'suggested' way to disable X Windows.."
date: 2006-03-26
forum: Server Platforms
---

### Post by cowmix on 2006-03-26
I do not want X Windows loading when my server boots.. what is the Ubuntu suggested way to do this?

thanks!

---

### Post by vyruss on 2006-03-26
[QUOTE=cowmix]I do not want X Windows loading when my server boots.. what is the Ubuntu suggested way to do this?
thanks![/QUOTE]
I'd do it like this:```
sudo apt-get install bum
```Then go to System -> Administration -> BootUp-Manager
Uncheck gdm (Gnome Display Manager)
Click on Apply, Click on Quit

---

