---
title: "Server boot up hangs"
date: 2008-10-31
forum: Server Platforms
---

### Post by ajwak95 on 2008-10-31
Hey all, I just upgraded to ubuntu server 8.10, and when I try and log in, it hangs where my mouse is displayed, but nothing else is. Please help.

---

### Post by ajwak95 on 2008-10-31
sorry, it is the login!

---

### Post by cariboo on 2008-10-31
You can't use a mouse on a server install. :) If it is hanging at the login screen, more then likely your graphics card is misconfigured. Try starting in recovery mode and at the menu select xfix, this should get you a working /etc/X11/xorg.conf file.

Jim

---

