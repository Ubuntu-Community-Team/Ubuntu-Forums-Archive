---
title: "Five ways to switch between workspaces in Ubuntu"
date: 2010-12-21
forum: Ubuntu Studio
---

### Post by JC Cheloven on 2010-12-21
> **Zaithyn Galter said:**
> 
[FONT=arial]***The list isn’t exhaustive so feel free to share your preferred method in the comments.***[/FONT]
Well, perhaps this belongs more to a general forum, but anyway:

My favourite method is to install compizconfig settings manager and use it to assign 
button4 = move one workspace left
button5 = move one workspace right

So, when hovering the mouse to an empty area of the desktop, scrolling the mouse wheel moves me to the other worspaces.

Cheers

---

### Post by mango42 on 2010-12-29
This thread prompts me to ask is there a way to 'embed' workspace switching in a script?

What I would like to do in Ubuntu Studio 10.04 on a 1024x768 Thinkpad (no Compiz) is to boot up and automagically have the following loaded into...
 
Screen 1 - Qtractor
Screen 2 - Hydrogen
Screen 3 - QJackCtl and ZynSubAddFX
Screen 4 - Patchage and Nautilus

...not that I could write the script anyway but I'm sure there's one out there I could modify...

:popcorn:

---

### Post by AutoStatic on 2010-12-29
mango42, try the **wmctrl** package, that should do exactly what you want. I think it's something like **wmctrl -r Qtractor -t 0**. But it depends on the window manager you're using.

---

### Post by mango42 on 2010-12-30
Many thanks for that. You are a mine of information ;-)

---

