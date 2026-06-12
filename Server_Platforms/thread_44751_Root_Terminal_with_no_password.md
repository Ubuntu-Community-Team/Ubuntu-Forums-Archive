---
title: "Root Terminal with no password??"
date: 2005-06-27
forum: Server Platforms
---

### Post by kxs on 2005-06-27
Is it normal that Root Terminal in Gnome doesn`t ask me for password?
Even if it is, how to change it?

---

### Post by Lunde on 2005-06-27
[QUOTE=kxs]Is it normal that Root Terminal in Gnome doesn`t ask me for password?
Even if it is, how to change it?[/QUOTE]
 No it's not normal unless you have recently opened another application that requires the root password. Log out and back in again and try and see if the password box apears.

Did this help?

---

### Post by kxs on 2005-06-27
thanks, it looks like that was the problem :-)
but for how long the root password works? and is there a way that programs would ask for root password every time, no matter what?

-------------------

and another problem is that when few programs start without root password the same way as Root Terminal 2 windows start. I mean one appears and another one is on Gnome Panel and disappears after a while. I can live with that but it bugs me off sometimes  :-?

---

### Post by Lunde on 2005-06-27
Sorry I can't answere that, don't know where the configuration is located

---

### Post by kxs on 2005-06-27
:) Found the answer here:
[http://ubuntuforums.org/showpost.php?p=214170&postcount=6](http://ubuntuforums.org/showpost.php?p=214170&postcount=6) 
> $sudo visudo

and adding this line beneath # Defaults
will set timeout to 30 instead of default 15 minutes :

Defaults:ALL timestamp_timeout=30
except that i`ve changed the timeout to 0

---

### Post by Lunde on 2005-06-28
[QUOTE=kxs]:) Found the answer here:
[http://ubuntuforums.org/showpost.php?p=214170&postcount=6](http://ubuntuforums.org/showpost.php?p=214170&postcount=6) 

except that i`ve changed the timeout to 0[/QUOTE]
 thanks for posting it

---

