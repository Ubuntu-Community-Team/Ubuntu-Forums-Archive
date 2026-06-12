---
title: "I propose an alternative to panels and docks"
date: 2008-11-15
forum: Ubuntu Brainstorm
---

### Post by HungryMan on 2008-11-15
I find docks and panels clunky. It takes quite some time to navigate through them, and seeing them on Linux plainly reminds me of OSX and Windows. I don't want these methods, they're not smart and fast enough. I want to share my idea on a new navigator.

I thought of this.[ATTACH]92750[/ATTACH]
(pardon the ugliness, but this is only a mock-up made in GIMP:)), a  ROUND navigator (ps i haven't called it anything yet)

Now, I do not have the coding knowledge to implement this, but I just want to share the idea. I repeat, THESE ARE IDEAS ONLY, AND IS NOT AN ACTUAL PROGRAM. Though it would be cool if we had this.

The icons on the outer ring are equivalent to the task list. Now, the icons needn't react to hovering and clicking like AWN, but it still needs a glow icon to notify if changes happened in the window and to differentiate the active window from the inactive ones. This mock-up can only hold 13 tasks icons, the only suggestion I can think of to fix that is to add a button that moves to the next "page" of the task list. I go against scrolling that part as it would be too slow and would defeat the purpose of this navigator.

the icons in the center are the notification icons. This mock-up can hold 2 rows with 4 icons each, how to add that, I still don't have an idea.

[ATTACH]92749[/ATTACH]
if you click the upper right quadrant, it would bring up a menu similar to the custom gnome menu, only instead of arranging it "applications,places,system", I changed it to "system,places,applications" so once you click on that button, the first thing that becomes clickable is the applications menu. Also I'd prefer if icons were used instead of the words "system", "places" and applications", why? read on :)

at the bottom of the menu is a place to put plugins (maybe gnome applets because force quit, and sticky notes are applets, but the downside of this is it'll be gnome only mwahahaha :twisted:... evil evil me). once again, the problem here is space.

oh, and I don't really mind about this feature much:
[ATTACH]92748[/ATTACH]
rotating the outer ring (that's why I didn't want words in the menu). This is good because you can position the navigator anywhere and anyway you want. And so I have something to play with :tongue:

The other thing I haven't thought about much is invocation. I've thought of some ideas:
1. a small icon that invokes the whole navigator - but this gets in the way of some programs
2. if you press or hold a key combination, it would invoke the navigator, near the position of the mouse cursor - nice and fast, but makes it feel modular and what if the cursor was at the edge of the screen?

Any ideas are welcome, but this is only in my mind. I do not have the coding knowledge and time to make this.

Deep in my mind, I'm praying [-o< that someone would do this... hahaha

---

### Post by Izek on 2008-11-15
It looks good, but it reminds me too much of the mock Windows seven and stardock.

---

### Post by HungryMan on 2008-11-15
oooh... haven't seen stardock yet, only objectdock from inspirat

---

### Post by amauk on 2008-11-15
A few things you may not have considered

[Fitts' Law]("http://en.wikipedia.org/wiki/Fitts%27s_law")
[Hick's Law]("http://en.wikipedia.org/wiki/Hick%27s_law")

Absolute must-read if you're considering UI design
You can skip the maths parts, but understand what they're saying, especially the "infinite width" concept - it's the reason most OS interfaces are placed on the edges of the screen

---

### Post by Izek on 2008-11-15
> **HungryMan said:**
> oooh... haven't seen stardock yet, only objectdock from inspirat

You mean rocket dock from Inspiriat Bricopack. ObjectDock IS Stardock's dock.

---

### Post by HungryMan on 2008-11-15
> **amauk said:**
> A few things you may not have considered

[Fitts' Law]("http://en.wikipedia.org/wiki/Fitts%27s_law")
[Hick's Law]("http://en.wikipedia.org/wiki/Hick%27s_law")

Absolute must-read if you're considering UI design
You can skip the maths parts, but understand what they're saying, especially the "infinite width" concept - it's the reason most OS interfaces are placed on the edges of the screen

Thanks for the link... more clicking brought me to pie menus. That's what I've been thinking off since last year. A round menu, because linear menus require more travelling time, the only downside (I think) of pie menus is the limited space.

The Sims' uses a pie menu, but once the choices exceed 8 (i think,haven't played in a long while), a second ring is created outside the first, but once the second ring has exceeded its limit, the exceeding choices aren't shown.

As for UI designing, I don't think so... this is all a pipe dream to me.:(

---

### Post by sirjoebob on 2008-11-15
This is a pretty good idea but (as much as I hate to say it) it looks like Microsoft beat you to it. I think someone should pursue it as an optional dock/panel replacement and would be a nice addition to screenlets, desklets, etc. It would also be a cool option for an exisiting dock.

The only problem I have with it would be the logistics of where it would be placed. It seems like it would undoubtedly be in the way of web browser windows, etc. Unless it was made too small to be useful. I am not discouraging it, rather the opposite. I just don't see myself dropping Gnome-Panel and AWN for it. :)

---

### Post by yaknowwat on 2008-11-16
[http://www.kde-look.org/content/show.php/KPlanetaryMenu+](http://www.kde-look.org/content/show.php/KPlanetaryMenu+)[idea]?content=88162

[http://code.google.com/p/circular-application-menu/](http://code.google.com/p/circular-application-menu/)

Stuff like that ?

---

### Post by alwayshere on 2008-11-16
something like a stargate  shape with sounds to match would rock a one stop shop for all desktop tasks  :guitar:

---

### Post by HungryMan on 2008-11-16
[QUOTE=yaknowwat][http://www.kde-look.org/content/show.php/KPlanetaryMenu+](http://www.kde-look.org/content/show.php/KPlanetaryMenu+)[idea]?content=88162

[http://code.google.com/p/circular-application-menu/](http://code.google.com/p/circular-application-menu/)

Stuff like that ?[/QUOTE]

yup, hey!! the second one was what I was looking for! the first link doesn't work, and I don't really like kde apps on gnome much... they stand out from my gtk apps and it doesn't look that nice (though not unbearably ugly).


[QUOTE=sirjoebob]The only problem I have with it would be the logistics of where it would be placed. It seems like it would undoubtedly be in the way of web browser windows, etc. Unless it was made too small to be useful. I am not discouraging it, rather the opposite. I just don't see myself dropping Gnome-Panel and AWN for it. [/QUOTE]

good point, It would get in my way which awn and gnome-panel/s do sometimes. perhaps you could invoke it if you pressed a key combination or something, but it would make it pretty modular or you could edge hide it or something.

---

### Post by HungryMan on 2008-11-16
yaknowwat - can't compile it...

when I make it, says stuff like:
```

...
Package gtk+-2.0 was not found in the pkg-config search path.
Perhaps you should add the directory containing `gtk+-2.0.pc'
to the PKG_CONFIG_PATH environment variable
No package 'gtk+-2.0' found
Package gnome-desktop-2.0 was not found in the pkg-config search path.
Perhaps you should add the directory containing `gnome-desktop-2.0.pc'
to the PKG_CONFIG_PATH environment variable
No package 'gnome-desktop-2.0' found
...

```

and other errors, because package gtk can't be found. I searched synaptic
for gtk+-2.0 and it didn't find it, same with gnome-desktop-2.0. This is my first time to install from SVN. Any help will be appreciated. Thanks

---

### Post by HungryMan on 2008-11-16
never mind... found a deb package of it. :)

---

