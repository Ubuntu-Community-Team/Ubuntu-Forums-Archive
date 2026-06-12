---
title: "after upgrade 5.19 to 5.20 desktop icons don't open folders"
date: 2020-10-18
forum: Ubuntu/Debian BASED
---

### Post by phileconte on 2020-10-18
Hi there,
I've upgraded from KDE plasma 5.19.5 to 5.20 and since that, the   icons on the desktop which normally open the dedicated folders on the  hard drive don't work. A click open a window which says (excuse the  translation from French) : this will open the software "name of the  folder" and an error occurs. I have tried to rebuild a new icon without  any success (same result). However, I can open the folder with a right  click  on the icon then / open with / Dolphin which is far more  complicated than a simple left click. 
A help to fix this bug would be very appreciated,
Thanks

---

### Post by phileconte on 2020-10-18
to dig a little deeper, the icon on the desktop points to /home/.local/share/plasma_icons, don't know if it can help...

---

### Post by ActionParsnip on 2020-10-18
How did you upgrade? What steps did you take? Did you add a PPA or was it regular updates?what is the output of:
```

lsb_release -a; uname -a

```
Thanks

---

### Post by phileconte on 2020-10-26
Sorry for the delay, I've seen that you had responded
I've updated using Discover as usual. Here is the response:
Thanks for your help
[HTML]philippe@philippe-XPS-13:~$ lsb_release -a; uname -a 
No LSB modules are available. 
Distributor ID: Neon 
Description:    KDE neon User Edition 5.20 
Release:        20.04 
Codename:       focal 
Linux philippe-XPS-13 5.4.0-52-generic #57-Ubuntu SMP Thu Oct 15 10:57:00 UTC 2020 x86_64 x86_64 x86
_64 GNU/Linux 
philippe@philippe-XPS-13:~$
[/HTML]
[FONT=monospace][COLOR=#54ff54]****[/COLOR][COLOR=#000000][/COLOR][COLOR=#5454ff]****[/COLOR][COLOR=#000000][/COLOR][/FONT]

---

### Post by uRock on 2020-10-26
Moved to *Other OS* support section.

---

