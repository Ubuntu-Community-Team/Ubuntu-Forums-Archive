---
title: "I wish gnome-panel was more flexible - guess i wont have to worry for much longer"
date: 2009-08-28
forum: The Cafe
---

### Post by pelle.k on 2009-08-28
I really hope the new **_gnome-shell_** will kill of the panel that has served us well for so long. Nothing is very consistent when using a gnome-panel size other than 24 pixels in height. It's not very pretty, it doesn't scale well, and it not very configurable. I'm attaching a screenshot of my panel in 52 pixels in height vs a mockup i gimped. My mockup may not speak to everyone, but the original gnome-panel surely looks a bit odd at that pixel height.
Out with the old, in with the new.

---

### Post by nothingspecial on 2009-08-28
```
sudo mv /usr/bin/gnome-panel ~/.panel
```

Death to the mouse ;)

---

### Post by joey-elijah on 2009-08-28
> **pelle.k said:**
> I really hope the new **_gnome-shell_** will kill of the panel that has served us well for so long. Nothing is very consistent when using a gnome-panel size other than 24 pixels in height. It's not very pretty, it doesn't scale well, and it not very configurable. I'm attaching a screenshot of my panel in 52 pixels in height vs a mockup i gimped. My mockup may not speak to everyone, but the original gnome-panel surely looks a bit odd at that pixel height.
Out with the old, in with the new.

i love the idea behind that mockup actually! it looks awesome.

---

### Post by pelle.k on 2009-08-28
> i love the idea behind that mockup actually! it looks awesome.
Yeah, i like it too. But it's never gonna happen with gnome-panel 2.X, but that's what I would have liked it to be. containers, padding, multiple rows for status-icons, proper sizes for applets, possibility to have text under icons instead of to the right. All that's missing in the current gnome-panel.
I guess it's no secret the gnome developers do don't do "pretty", but rather "functional". I'm hoping the new "gnome shell" will bin a lot of the legacy code, and rebuild something new, and aesthetically pleasing, this time around.
i mean, just look at the gnome panel in the previous attached screenie at 52 pixels, what a freakin mess. It's embarrassing.

I'm a sucker for looks. If that makes me shallow, then so be it. My argument is (and has always been) that the panel is the face of the OS, it's the No 1 gui. It's what you see when you boot your OS up, and when you shut it down. And most time in between. It should really be a priority, looks wise. And it should, preferably, be more configurable than the rest of the system, because it's always gonna be in your face.

---

### Post by Warpnow on 2009-08-28
> **nothingspecial said:**
> ```
sudo mv /usr/bin/gnome-panel ~/.panel
```

Death to the mouse ;)

Will that command kill the panel entirely?

---

### Post by nothingspecial on 2009-08-29
Yup, but you`re only moving it. You can move it back if you don`t like it.

---

### Post by yabbadabbadont on 2009-08-29
> **nothingspecial said:**
> Yup, but you`re only moving it. You can move it back if you don`t like it.

I think that this is the more elegant solution.  ;)
```
sudo chmod a-x /usr/bin/gnome-panel
```

---

### Post by nothingspecial on 2009-08-29
Yes, it probably is.

Do you not like panels either?

I refer you to a much earlier post of mine [[COLOR="Magenta"]here[/COLOR]]("http://newyork.ubuntuforums.org/showpost.php?p=7022733&postcount=348")

---

### Post by kerry_s on 2009-08-29
wow, 52 is huge, what's your screen size?
i think its because the panel is using both png & svg icons.

mine looks really distorted at that size.

---

### Post by pelle.k on 2009-08-29
> wow, 52 is huge, what's your screen size?
i think its because the panel is using both png & svg icons.
I use 1650x1080 so i have plenty of space to spare. But my point is that even at 32 pixels in height, things start to look rather odd.
If one could configure, say the notification area, to stay at a certain size, double the rows when possible, make use of some padding (and optional borders) it would look rather good. Also the main menu is also highly inflexible - it doesn't do any other look other than the default. I mean, when the panel grows, the menu stays exactly the same (not your menu, but the ubuntu default). It look ridiculous! Why cant one have icons (that scale - that seems to be lacking at some panel widgets) for each menu alternative (Applications, Places, System), or both, like the panel of nautilus? That would scale well.
However, Gnome 2.X is soon going to be what KDE3 was to KDE4, so there's not much to do about it now, but it may serve as a remainder not to do the same mistakes in gnome 3.0.

---

### Post by Copernicus1234 on 2009-08-29
If you like that look, perhaps you like this application:

[http://beatniksoftware.com/gimmie/Main_Page](http://beatniksoftware.com/gimmie/Main_Page)

---

### Post by yabbadabbadont on 2009-08-29
> **nothingspecial said:**
> Do you not like panels either?

I don't have a problem with panels that do just what I need, and no more.  I use Openbox with tint2 for the taskbar, systray, and clock.  That's all I want from a panel.

---

### Post by nothingspecial on 2009-08-29
I use gnome on the main family pc. I just don`t use panels, docks or a mouse. gnome-do, keyboard shortcuts and the shell just suit me fine

---

### Post by DigitalDuality on 2009-08-29
thank god you don't do UI design.   And from the looks of it, gnome-shell and gnome 3.x looks more awful than kde 4.x

---

### Post by pelle.k on 2009-08-29
> thank god you don't do UI design. And from the looks of it, gnome-shell and gnome 3.x looks more awful than kde 4.x
Well i thank you for that quick stab. I never intended it to look stunning, nor was it the point of the mockup. It was about how inflexible it is on non standard resolutions, and how it handles icon and applet sizing sizing etc.
But for the sake of argument, applets are expanding full width in my example, while tray icons are stacked in rows due to the panel height. Just like in kde4. If you want to pick on the container border, that's fine. It was a one minute job. And furthermore, if it was "real", it would be dependent on the actual gtkrc theme in use.
The only other modifications i made was the encapsulation of the gnome menu, and the file-browser-applet with buttons (and the actual buttons are not made up, but clearlooks buttons). Again, a one minute job, and for the sake of demonstrating people *may* want clickable items on the panel to appear as buttons . Or not. That should be a preference. Also this demonstrates a how one may want to place icons over the text, just like in any other panel, should one want to.
It's not about how i would like the panel to look like by default. Looks wise, i would prefer if the gnome panel was as themeable as kde4's panel. But this demonstration was not so much as the actual theme of the gnome panel, as how little we can configure it to behave.
It was more an example to how inflexible the gnome-panel is at other pixel heights other than 24 pixels in height. I did not invent the gtkrc used to construct the panel, and in fact, you are severly limited in that respect when doing a theme for gnome/gtk.
You have very few options when themeing the panel, and just as few when selecting the behaviour and apperance of applets on the panel.

---

### Post by RATM_Owns on 2009-08-29
tint2 > gnome-panel

---

