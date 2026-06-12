---
title: "Guild Wars Won't Run"
date: 2009-06-15
forum: Wine
---

### Post by Alex L on 2009-06-15
I've read through quite a few threads and tried various solutions. I'm not getting quite the same problem though and I can't find a way to fix this. If I've simply missed the thread, please paste the link and I'll try it. I will mark this as solved when I'm done. Thanks in advance for your help.

First off, I'm using Ubuntu 9.04 (32 bit) with an AMD duel core Athlon x64 processor, ATI Radeon HD 4650. I can find my other specs if needed or you can give me a terminal command that will most likly know it all anyway.

I have the current version of WINE that is in the Add/Remove programs in the applications menu.

Before I get onto Guild Wars, note when I open Sportify in Wine, my screen flashes violently while it is loading and logging in but one the application is launched, it all goes smooth again and works just like it does in Windows.

I have activated the ATI driver in the Hardware drivers.

Right then...

When I load Guild Wars, the whole screen flashes violently. It loads the files and gets to the login screen (see below). All the while this is still flashing and making parts of the screen transparent which roll upwards in bars (you probably see what I mean in the picture). 

[[IMG]http://img411.imageshack.us/img411/9937/screenshotpto.th.png[/IMG]]("http://img411.imageshack.us/i/screenshotpto.png/")

At this screen there should be a login box and text should be where the red lines are (note the red lines do no always appear). I can just about log in if I'm lucky, in which case I see the character selection screen which is in a similar state. It might be worth me mentioning they are missing a lot of detail. They look like the shells of the characters but they are in skin tone (even the armour, hair, eyes ect) and they have gaping holes in them. I was unable to get further than this.

---

### Post by cogadh on 2009-06-15
Try using the Universal Linux Launcher for NCSoft games. It's no longer being actively developed, but it already supports GW:
[http://sourceforge.net/projects/ull/](http://sourceforge.net/projects/ull/)

---

### Post by wubiubiubi on 2009-06-15
Try opening applications->wine->configure wine. Then set the version of windows to windows 98. I don't know if this will help you but setting wine to win98 very very often helps with lots of problems in guild wars. 
Also, because the "violent flashing" happens in other apps under wine, it's possible that wine doesn't fully support your video card, in which case the only possible fix is updating to the latest version of wine (the "development version"). Although this is no guaranteed fix, newer versions may have fuller support for your graphics card.

---

### Post by Alex L on 2009-06-15
> **cogadh said:**
> Try using the Universal Linux Launcher for NCSoft games. It's no longer being actively developed, but it already supports GW:
[http://sourceforge.net/projects/ull/](http://sourceforge.net/projects/ull/)

I've tried this but I'm unable to get the thing installed. I get an error message which is shown how to fix in the guide. I follow the instructions for the fix but still get the same error. I will look for a tutorial on how to install it correctly later.

> **wubiubiubi said:**
> Try opening applications->wine->configure wine. Then set the version of windows to windows 98. I don't know if this will help you but setting wine to win98 very very often helps with lots of problems in guild wars. 
Also, because the "violent flashing" happens in other apps under wine, it's possible that wine doesn't fully support your video card, in which case the only possible fix is updating to the latest version of wine (the "development version"). Although this is no guaranteed fix, newer versions may have fuller support for your graphics card.

This is better, I can login ect, however the game is very laggy and I still get the blinding flashes. How to I get the development version of WINE?

EDIT: I just flicked back and everything is working perfectly :s

Thanks - Solved

---

