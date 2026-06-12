---
title: "Help with Samba PDC XP Logon"
date: 2010-05-11
forum: Server Platforms
---

### Post by pgun90 on 2010-05-11
Hei

I have one Ubuntu server 9.04 with samba domain. I have one Xp pro in this domain. When the XP computer logon, the theme is classic... How can I change that? I want the standard XP theme...... 

Thanks for the help

-pgun90

---

### Post by gobbledigook on 2010-05-11
samba doesn't define the "look" or "feel" of the connection - look at your windows settings

---

### Post by pgun90 on 2010-05-11
You know how i can fix it? I don't want the classic look.... Something I can install to manage it?

---

### Post by wrp on 2010-05-11
It is set in Windows. I can't remember where 
Try right clicking on the desktop and looking at the options there. 
Alternatively Settings on the start menu.
It IS possible to control this from the PDC using policy settings. See if you have a file NTConfig.POL in the Network logon share. 
It is very well explained at 
[http://www.pcc-services.com/articles/implement_sys_policies.html](http://www.pcc-services.com/articles/implement_sys_policies.html)
but this is pretty sophisticated for most of us and I suspect that your profile has been accidentally changed to the "classic" look. Once you set it back it should be fine. 
(Actually I prefer classic ...)

---

