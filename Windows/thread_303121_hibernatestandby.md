---
title: "hibernate/standby"
date: 2006-11-19
forum: Windows
---

### Post by Mazen on 2006-11-19
does anyone know how i can get both the hibernate AND the standby button when i click on the start>turn off computer button?
thanks

---

### Post by mofokuban on 2006-11-20
> **Mazen said:**
> does anyone know how i can get both the hibernate AND the standby button when i click on the start>turn off computer button?
thanks
Make sure your power settings allow for Hibernation.

This can all be done through the Control Panel option (Power Options or something similar, I can't remember).

---

### Post by drFUNK on 2006-11-20
It's planned to be part of XP's 3rd service pack, but if you want to do it now, you'll have to edit the registry:
[QUOTE=http://jkontherun.blogs.com/jkontherun/2006/07/put_the_hiberna.html]In the registry, create this key:
\HKEY_LOCAL_MACHINE\SOFTWARE\Policies\Microsoft\Windows\System\Shutdown
Create a DWORD value named ShowHibernationButton and set its data to 1.  Now, go ahead and click Start, Shutdown, and you'll see all four buttons available simultaneously.
 
Lastly, you can go to the Display Properties' Power Management applet and choose "Tell me what to do" when you flick the Power switch and get all the options at your fingertips![/QUOTE]

---

