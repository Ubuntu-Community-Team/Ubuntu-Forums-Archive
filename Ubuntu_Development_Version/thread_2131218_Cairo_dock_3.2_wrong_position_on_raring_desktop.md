---
title: "Cairo dock 3.2 wrong position on raring desktop"
date: 2013-04-01
forum: Ubuntu Development Version
---

### Post by leo4kusuma on 2013-04-01
I had tried until three times, may be more to fix this trouble of Cairo Dock v3.2 position on my Raring Desktop. I don't know why, Cairo Dock always show wrong position, as you can see on my pict attached here. I must be at the center on the edge of bottom. I can fix it, by configuring via System -> Composition. Then, give thick on the Composition, click Apply, and remove thick on the Composition, then Apply. But can you explain why Cairo Dock show wrong position on my Raring desktop? Note, I run Cairo Dock with OpenGL.

[IMG]http://img198.imageshack.us/img198/3886/myraring2.jpg[/IMG]

---

### Post by Frogs Hair on 2013-04-02
It could have something to do with the fact that 13.04 is still beta. Although 13.04 has reached beta freeze there are still many updates forth coming. I have had 60 + the last 2 days. You may have to wait for someone who is running Cairo Dock on 13.04.

---

### Post by Elfy on 2013-04-02
*Thread moved to **Ubuntu +1 (Raring Ringtail)**.*

---

### Post by xc3RnbFO8P on 2013-04-02
> **leo4kusuma said:**
> I had tried until three times, may be more to fix this trouble of Cairo Dock v3.2 position on my Raring Desktop. I don't know why, Cairo Dock always show wrong position, as you can see on my pict attached here. I must be at the center on the edge of bottom. I can fix it, by configuring via System -> Composition. Then, give thick on the Composition, click Apply, and remove thick on the Composition, then Apply. But can you explain why Cairo Dock show wrong position on my Raring desktop? Note, I run Cairo Dock with OpenGL.



In Compiz Settings Manager try to uncheck Unity Plugin,
and log out

---

### Post by ManamiVixen on 2013-04-02
[B]DO NOT UNCHECK THE UNITY PLUGIN, YOU WILL LOOSE THE WHOLE DESKTOP!
[/B]
Instead, disable multiple desktops. In Unity, multiple desktops are treated as congruent so Cairo-Dock is being stretch between screen 1 and 2. with Multiple Desktops disabled, there will be one desktop and Cairo will be centered.

---

### Post by zika on 2013-04-02
> **Ringi said:**
> In Compiz Settings Manager try to uncheck Unity Plugin,
and log out
If You uncheck Unity and do not have any other WM how will You be able to get it back...?
I know, it could be done throgh CLI but, I'm not sure everybody know how...
Be carefull with Your advices...
Let's say that I might be wrong, but I would like that ergo that way I would learn something new...

---

### Post by xc3RnbFO8P on 2013-04-02
@ManamiVixen and zika, do you have cairo dock installed?

---

### Post by zika on 2013-04-02
> **Ringi said:**
> @ManamiVixen and zika, do you have cairo dock installed?No, I do not...
I said I'll learn something new to me... Shoot... ;)

---

### Post by ManamiVixen on 2013-04-02
No, not anymore. But I know how it works in relation to Unity.

---

### Post by xc3RnbFO8P on 2013-04-02
You can login to Cairo Dock with opengl, then you have to disable Unity plugin,
as he say: " Note, I run Cairo Dock with OpenGL."

 you're giving me a heart attack :)

---

### Post by mc4man on 2013-04-02
> **zika said:**
> If You uncheck Unity and do not have any other WM how will You be able to get it back...?
I know, it could be done throgh CLI but, I'm not sure everybody know how...
Be carefull with Your advices...
Let's say that I might be wrong, but I would like that ergo that way I would learn something new...
Being that's it's mainly a plugin for the Wm (compiz),  you can disable unity without too much going away. To re-enable just simply open ccsm & enable.

(running a ubuntu session without unity may need a few adjustments because of all the gschemas/overrides, ect., but wouldn't be to hard to work out.

---

### Post by fabounet on 2013-04-03
Instead of disabling Unity from ccsm, prefer to log into a Cairo-dock session.
This way, you can have a light session with cairo-dock, without messing up with the Unity session.

PS: you may have to enable the application switcher (alt+tab) in ccsm.

---

### Post by zika on 2013-04-03
> **mc4man said:**
> Being that's it's mainly a plugin for the Wm (compiz),  you can disable unity without too much going away. To re-enable just simply open ccsm & enable.

(running a ubuntu session without unity may need a few adjustments because of all the gschemas/overrides, ect., but wouldn't be to hard to work out.I'll have to play (again, after quite a time) with Unity... I, usually, start it via startx/xinit so I'll have to find a way to start compiz without Unity... ;)
```
exec /usr/bin/ck-launch-session /usr/bin/gnome-session --session=ubuntu
```might do the trick, I'll try...
Update&#8321;: Yeap, that works, and that doesn't have Unity started... Thank You for making me try this... Downside: custom keyboard shortcuts still do not work, but that is because I have all GS PPAs turned on... Upside: I get clean black screen and no bars, panels, notnihg... Nice...
As I've wrote, I like that I've learned something new, again...
[http://www.youtube.com/watch?v=3PszMaZ5Ipk](http://www.youtube.com/watch?v=3PszMaZ5Ipk)

---

### Post by Cavsfan on 2013-04-03
Never had a problem with Cairo Dock 3.2 in Gnome fallback or Unity.
Don't know what to tell you. :P

[[IMG]http://ompldr.org/taHo4MA[/IMG]]("http://ompldr.org/vaHo4MA/Screenshot 2013-04-03.png")

---

### Post by leo4kusuma on 2013-04-10
RARING UPDATE ON APRIL 11st 2013 -> FIX MY TROUBLE ON CAIRO DOCK v3.2. 
Well done everybody. After waiting for several days, Unity desktop fix the desktop problem for Cairo Dock. There are several important updates on April 11st 2013, not only fix for Cairo dock, also fix for Wallch. Thank you!

---

