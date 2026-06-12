---
title: "Does anyone know how to fix this window size?"
date: 2010-12-25
forum: Wine
---

### Post by flakzeus on 2010-12-25
I've been fiddling around with this for a couple of days now, modifying the games resolution, the wine virtual desktop resolution, etc. I need to run this game in windowed mode, and I set the screen resolution via it's config file. However, the only thing that it changes is the game resolution and not the actual size of the window. Any help?
Thanks!

[IMG]http://i.imgur.com/KyquQ.jpg[/IMG]

---

### Post by cogadh on 2010-12-27
Looks like you just need to configure Wine's virtual desktop and the game to the same resolution. Based on what I'm seeing there, it looks like the game is set to a much higher resolution than the virtual desktop and since Wine's virtual desktop cannot size up from whatever you set it to, the game's higher resolution "falls off" the virtual desktop. You have two options: go into winecfg and change the virtual desktop setting to the same res as the game or change the game's config so that it has the same res as Wine.

---

