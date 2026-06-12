---
title: "Help me test transparency bug"
date: 2012-04-01
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by sandyd on 2012-04-01
I recently discovered by accident that the Taskbar App Menus (Global Menu) are actually not hidden - instead the text is just turned black.

I discovered this when I turned the taskbar transparent. Is there some way to stop the text from doing this?

---

### Post by Bhawani007 on 2012-04-01
Nope global menu is hidden.
I personally use transparent taskbar. there might be problem with your unity settings. Most of the unity setting problems are caused by CCSM.

---

### Post by sandyd on 2012-04-01
> **Bhawani007 said:**
> Nope global menu is hidden.
I personally use transparent taskbar. there might be problem with your unity settings. Most of the unity setting problems are caused by CCSM.
Look at this carefully.

Actually, I think its a bug.
If I open the window, the black text overlays don't appear until I summon the menus.
hmm...

---

### Post by sandyd on 2012-04-01
I recently set out to personalize Ubuntu a bit, and I turned the taskbar transparent.
Normally, this bug wouldn't have been apparent otherwise.

I discovered that in the global menu area, text is kept as an underlay.

For example, if I hover over the global menu area to open the app menu, the name of the program will be colored in black, and sent to the back. After a while, this dissapears.

Please test by setting panel opacity to 0 in compizconfig-settings-manager -> Unity -> Experimental.

[https://bugs.launchpad.net/unity/+bug/924592](https://bugs.launchpad.net/unity/+bug/924592)

Screenshot is attached to the bug

---

### Post by jasonsmith01 on 2012-04-01
It does effect me and has been marked accordingly.

Incidentally have you noticed that while you have the taskbar transparent and you change wallpapers it retains the imagine from the previous wallpaper under the taskbar??

---

### Post by stinkeye on 2012-04-01
Happens here as well.
The global menu is drawn black when inactive, so shows in a 100% transparent 
panel when using a light wallpaper.
Bug [**_[COLOR="DarkRed"]HERE[/COLOR]_**]("https://bugs.launchpad.net/unity/+bug/924592")

---

### Post by mc4man on 2012-04-01
This has been an issue for almost 2 months, though there used to be a workaround until just  recently.
That would have been to set the opacity to 0.0100 which would look the same as 0.0000
Now 0.0100 remains colored so no relief there, I'd actually rather see the black text which usually disappears after several seconds (not always

Hopefully one or the other or both are fixed - 
[https://bugs.launchpad.net/ubuntu/+source/unity/+bug/963505](https://bugs.launchpad.net/ubuntu/+source/unity/+bug/963505)

---

### Post by cariboo on 2012-04-02
Merged two threads on the same subject

---

### Post by stinkeye on 2012-04-02
> **mc4man said:**
> This has been an issue for almost 2 months, though there used to be a workaround until just  recently.
That would have been to set the opacity to 0.0100 which would look the same as 0.0000
Now 0.0100 remains colored so no relief there, I'd actually rather see the black text which usually disappears after several seconds (not always

Hopefully one or the other or both are fixed - 
[https://bugs.launchpad.net/ubuntu/+source/unity/+bug/963505](https://bugs.launchpad.net/ubuntu/+source/unity/+bug/963505)
I'm on 12.04 and it goes away when I set the transparency to 0.0100.
I like to use a conky under the panel for system indicators.
Because of the blur effect the conky won't show unless the panel is fully transparent.

---

### Post by sandyd on 2012-04-03
Just discovered:
Enable the JPEG plugin, use 0.01 for opacity.

---

### Post by mc4man on 2012-04-03
> **stinkeye said:**
> I'm on 12.04 and it goes away when I set the transparency to 0.0100.
I like to use a conky under the panel for system indicators.
Because of the blur effect the conky won't show unless the panel is fully transparent.
Yeah  - you definitely want full trans to work right. Myself either full or a 'proper' lower would work.
Atm once you hit 0.3000 or so there is no change here till 0.0000

Overall I think they've screwed this up pretty good this cycle, probably all resulting from the colored launcher business. The only thing that got better is the Dash blur, otherwise don't like how the panel & launcher are 'disconnected' color wise (unless you set the panel transparent
 - though I'm sure many think it's just great (most probably

---

