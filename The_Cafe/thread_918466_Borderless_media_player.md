---
title: "Borderless media player"
date: 2008-09-12
forum: The Cafe
---

### Post by aschwerin.moses on 2008-09-12
Hi... i would like to know if there is a borderless media player.. or can we make mplayer or totem borderless..????...

---

### Post by zmjjmz on 2008-09-12
Audacious works.
It doesn't play video though.

---

### Post by aschwerin.moses on 2008-09-12
I need it to play both.. audio and video

---

### Post by smartboyathome on 2008-09-12
You can make mplayer borderless. Look up any howto on XWinWrap (which allows you to use videos and screensavers as backgrounds), and you will find how to do this with mplayer.

---

### Post by aschwerin.moses on 2008-09-13
done that already... no luck :(

---

### Post by andrew.46 on 2008-09-15
Hi,

The svn MPlayer has a -noborder option:

>        -border
              Play movie with window border and decorations.  Since this is on
              by default, use -noborder to disable the standard window decorations.


  Andrew

---

### Post by 3rdalbum on 2008-09-15
You could use a titlebarless Metacity theme, or even the "nothing" theme which is completely borderless. Of course, it takes effect across all your windows, but just think of the screen space you'll save!

---

### Post by zekopeko on 2008-09-15
hmmm... if you use compiz perhaps you could specify totem or other media player to display without borders...?

EDIT:

yup! it can be done

open compiz config settings manager, go to window decorations and add this to "Decoration windows"

(any) & !(class=Totem)

you can use the plus botton and then grap on the window that you want borderless. i suggest that you use class and don't forget to invert your selection (thats what that ! is for)

also you can press H to remove the controls of totem.

EDIT EDIT: man you gotta love linux! :D

---

### Post by issih on 2008-09-15
In compiz it is dead easy....I just checked it was possible.

go into ccsm and into the Window Decorations plugin.

Then add the appropriate exception to the Decoration windows line:

by default it reads:

```
any
```

Something like:

```
(any) && !(class=totem)
```

should do it, I just used the little wizard you get by clicking to add to that line though.

That gave me a totally borderless totem window, big bonus is that you can use whatever media player you want :)

Hope that helps

Edit....TOO SLOW!!! :)

---

### Post by zekopeko on 2008-09-15
> Edit....TOO SLOW!!! :)
muahahahaha!!!

---

