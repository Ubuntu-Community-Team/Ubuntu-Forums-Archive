---
title: "WoW: Cataclysm Performance Issues"
date: 2010-12-09
forum: Wine
---

### Post by Ravenian on 2010-12-09
Hello everyone,
I've been using Ubuntu for just over 2 months now - I have to say it's nothing like I've ever tried before, and I am very satisfied with it, but I'm still trying to learn the ropes.
I'm a casual gamer and I've recently restarted playing World of Warcraft via Wine (a friend help me set it up): the one problem I have is that when I was under Windows, I used to play at around 50-60 fps on average. Now that I'm on Ubuntu 10.10, I'm stuck at around 10 even with the video details set to low.

I really have no idea why this might be. Is such a huge performance loss normal when playing games via Wine? Any tips? :)

---

### Post by amauk on 2010-12-09
are you using Direct3D or OpenGL?

Using Direct3D will penalise your performance, as it's a windows only graphics layer and is emulated by Wine
OpenGL is a native graphics layer, and doesn't need any emulation, so is a lot faster

Open up your Warcraft config file

Applications > Wine > Browse C: Drive
It's in Program Files/World of Warcraft/wtf/Config.wtf

Add this to the file, and save
```
SET gxApi "opengl"
```

---

### Post by Ravenian on 2010-12-09
Thank you, things have gotten slightly better now - I'm not at an average of 30fps. Better than 15!

---

### Post by amauk on 2010-12-09
You may also get a performance increase if you disable Compiz while playing
(Compiz being the 3D window environment (desktop cube and other things) that Ubuntu uses)

Install fusion-icon (search for it in the software centre)
It's a little icon in the notification area that allows you to disable and re-enable compiz

Disable prior to playing, and re-enable it again after

---

### Post by Ravenian on 2010-12-09
> **amauk said:**
> You may also get a performance increase if you disable Compiz while playing
(Compiz being the 3D window environment (desktop cube and other things) that Ubuntu uses)

Install fusion-icon (search for it in the software centre)
It's a little icon in the notification area that allows you to disable and re-enable compiz

Disable prior to playing, and re-enable it again after

I tried this last tip, and it's working so much better now.
Thanks a lot! :)

---

### Post by amauk on 2010-12-09
no problem

---

### Post by madjr on 2010-12-09
what was your video card?

---

### Post by alaukikyo on 2010-12-09
you can also make a new empty file on the desktop then rename it games booster
then open with gedit and paste 'metacity --replace'(without the quotes) then sace and go to properties ->permissions and then allow it to execute and double clicking it will disable compiz and improve speed.

you can also make a game booster off file with same instructions but with 'compiz --replace'  in the file it will re-enable the compiz effects

---

### Post by Ravenian on 2010-12-09
Thanks again for the tips.
My video card is rather old, it's an ATI radeon 4850. It has always worked fine though.

---

