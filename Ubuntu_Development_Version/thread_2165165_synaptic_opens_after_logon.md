---
title: "synaptic opens after logon"
date: 2013-08-03
forum: Ubuntu Development Version
---

### Post by ventrical on 2013-08-03
Is this the norm for Xubuntu?

saucy i386 xubuntu..

---

### Post by The Cog on 2013-08-03
It opens as soon as you log on? No. You probably had XFCE configured to restore sessions and logged out with synaptic running. 
I think what you need to do is to close all applications, then logout and check "Save sessions for future logins". Hopefully, this will the save "nothing running". 
Then log back in, make sure everything is still closed, then logout again, this time un-checking the box (so it doesn't save sessions in future).

There's a hidden folder that stores these sessions somewhere, but I forget where.

---

### Post by ventrical on 2013-08-03
> **The Cog said:**
> It opens as soon as you log on? No. You probably had XFCE configured to restore sessions and logged out with synaptic running. 
I think what you need to do is to close all applications, then logout and check "Save sessions for future logins". Hopefully, this will the save "nothing running". 
Then log back in, make sure everything is still closed, then logout again, this time un-checking the box (so it doesn't save sessions in future).

There's a hidden folder that stores these sessions somewhere, but I forget where.



Just perfect. :)

 I left my ff browser open, rebooted and it brought me right back to UbuForums without having to sign in.

Neat little tool.

thanks ..

regards..

---

### Post by ajgreeny on 2013-08-03
Just for info, saved sessions are all stored in ~/.cache/sessions.

---

### Post by ventrical on 2013-08-03
thnxs ;)

---

