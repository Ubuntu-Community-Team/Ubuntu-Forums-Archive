---
title: "lost wifi icon from panel"
date: 2015-06-17
forum: Ubuntu/Debian BASED
---

### Post by medspammer on 2015-06-17
Hi all ,
I have problem with my with ubuntu
in Xfce desktop
i lost my wifi icon from the panel
while i try : sudo nm-applet
I get it back but i want it to start automatique in startup
i try to add it in 
Setting -> Session and startup -> add ( sudo nm-applet )
But it still not showing in the panel .. ( only when i try it manuel )
i tried to add it to the /etc/rc.local ( above exit )
but still the same problem anyone can help me pls ..
to get the  wifi icon back or to start the command [ sudo nm-applet ] in the startup 
and thank you

---

### Post by ajgreeny on 2015-06-17
Don't start nm-applet as root but as your user, so use command **nm-applet** in your startup applications without sudo and you should have more luck.

However, nm-applet should already be in the list as one of the applications not editable by you, so something must have gone wrong somewhere else.

I have seen this problem in Lubuntu before, but not Xubuntu; are you actually using Xubuntu or have you simply added XFCE4 desktop to another DE system such as Lubuntu?

---

### Post by medspammer on 2015-06-17
I tried it but still the same problem...
i search in the internet about a solution but i haven't found it that's why i had posted it here 
( i use backbox )

---

### Post by coffeecat on 2015-06-17
> **medspammer said:**
> ( i use backbox )

*Thread moved to **Ubuntu/Debian BASED**.*

---

### Post by v3.xx on 2015-06-17
Not many blackbox users around, makes it tough.

Could you just reinstall the panel?

---

