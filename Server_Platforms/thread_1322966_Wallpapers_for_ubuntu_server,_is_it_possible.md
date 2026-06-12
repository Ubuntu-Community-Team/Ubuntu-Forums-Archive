---
title: "Wallpapers for ubuntu server, is it possible?"
date: 2009-11-11
forum: Server Platforms
---

### Post by Predatorian on 2009-11-11
howdy peeps,

i was just wondering, is it possible to set Ubuntu server up with a background wall paper? or would i have to set soemthing like xmonad up so i could have the option of doing that? i guess if my question is off topic, please move it, or if it needs to be cleared up, just ask away. thank you.

---

### Post by UltimatePisman on 2009-11-11
Ubuntu Server isn't graphical.
So the answer is no.

---

### Post by Simian Man on 2009-11-11
It doesn't come with an X-Server by default.  Without an X-Server you have no way of rendering a desktop or wallpaper or anything except for text.

If you really want a wallpaper, you will have to install the X-Server along with some window manager.  However for a server this is usually not that useful.

---

### Post by capscrew on 2009-11-11
> **Predatorian said:**
> howdy peeps,

i was just wondering, is it possible to set Ubuntu server up with a background wall paper? or would i have to set soemthing like xmonad up so i could have the option of doing that? ...

The direct answer is no, as others have said.  But you don't need to use the console directly either.  I always ssh to the server.  The remote host is running X-server and a windows manage.  If you use a Windows host you can use PuTTY to ssh.

---

