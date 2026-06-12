---
title: "Standalone Compiz and window-decorations in 14.04"
date: 2014-03-30
forum: Ubuntu Development Version
---

### Post by Jackson_Wiegman on 2014-03-30
I run a minimal server install on 13.04 where I use compiz (and gtk-window-decorator) for my GUI element. I am experimenting with 14.04 as it natively fixes a number of bugs I have encountered in my system, but compiz is no longer working like it used to - it appears that gtk-window-decorator has been deprecated in favour of Gtk3 theming  ([https://wiki.ubuntu.com/Unity/Theming](https://wiki.ubuntu.com/Unity/Theming)), so I am not getting any window decorations in my system.

I've searched around for a resource on how this Gtk3 themeing would integrate into a standalone Compiz but I am coming up empty, can anyone point me in the right direction?

---

### Post by xc3RnbFO8P on 2014-03-31
Install Compiz Config Settings Manager
and check Window Decoration

---

### Post by freebird54 on 2014-03-31
> **Ringi said:**
> Install Compiz Config Settings Manager
and check Window Decoration

One problem with that - it disables the Unity plugin if I try it!  SOME of the functions of the window decorator have apparently been subsumed into Unity (at least shading I guess) but it won't allow window decoration as a separate function for that reason.  There's a lot fewer available items in CCSM too ...

---

### Post by Mateusz Stachowski on 2014-03-31
> **freebird54 said:**
> One problem with that - it disables the Unity plugin if I try it!  SOME of the functions of the window decorator have apparently been subsumed into Unity (at least shading I guess) but it won't allow window decoration as a separate function for that reason.  There's a lot fewer available items in CCSM too ...

Correction the new decorations are entirely implemented in Unity and they use GTK 3 theming.

[https://code.launchpad.net/~3v1n0/unity/unity-decorations/+merge/202582](https://code.launchpad.net/~3v1n0/unity/unity-decorations/+merge/202582)

---

### Post by grahammechanical on 2014-03-31
AS for the missing options in CCSM, look in the software centre for compiz-plugins. That will get them back.

Regards.

---

### Post by freebird54 on 2014-04-01
Thanks for the info about the 'missing' options. I suspected that might be the case, but I was unsure to what degree they could still be used...perhaps they were removed for conflict, rather than for 'simplification' for the unwary :)  Does this mean I can bring back the cube? :D

Not that I need the cube...I have found other ways to get the functionality - but I guess I'll have to find out how theming works - as I can't find a 'pre-done' one that I like.  I was using a dark theme, but I coudn't find one with all the pieces as I want them -- perviously (12.04) I used a separate theme for windows than I did for the overall theme, and even the icons aren't apparently transferable between 12.04 and 14.04.  Yet another thing to learn I guess.

---

