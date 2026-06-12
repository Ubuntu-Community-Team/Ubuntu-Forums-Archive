---
title: "MX518 and Wine"
date: 2009-05-06
forum: Wine
---

### Post by Alethenorio on 2009-05-06
OK so here the deal:

The Logitech MX518 has 8 configurable buttons. Ubuntu seems to recognize the buttons just fine. The thumb buttons will work fine on firefox (Even though I'd like to be able disable that feature) and on the ubuntu mouse configuration, with the light bulb, the application switch button seems to be recognized just fine.

Having said that I cannot, in any way, get the application switch button to work on wine. I have researched for days, hundreds of different articles (Most of which are about getting the thumb buttons to work on firefox :S) without any success and tried loads of different configurations to different files, xmodmap, xorg.conf but nothing works.

I dont want the button to switch applications or any special thing, I just want to be able to hotkey the application switch button to my programs running on wine. Ventrillo won't recognize it and Wow won't recognize it.

My last resort would be trying to install the logitech drivers under wine but something tells me that is not gonna work.

Does anybody have any insight on this issue? Can we maybe get some brainstorming going to finally get this fixed?

Best Regards

Alex

---

### Post by cogadh on 2009-05-06
I don't have any insight into how you couold get it to work, but I can tell you that installing the drivers in Wine would be a waste of time. Windows drivers do not work in Wine:

[quote="Wine FAQ"]**3.4. Can I use Wine to install drivers for my hardware?**

No. With the possible future exception of some printer drivers, Wine requires your hardware to already be working on your operating system. The technical reason for this is that Wine, like most applications, runs in user mode and not kernel mode.[/quote]

---

### Post by Alethenorio on 2009-05-06
Yes that is exactly what I thought which is why I hope somebody has another idea.

I can't possibly be the only person trying to bind the application switch button to applications running on wine, can I?

---

### Post by Alethenorio on 2009-05-21
Thought I'd bump this. Issue still there, is it really not possible?

---

### Post by Alethenorio on 2009-06-15
Yet another bump. Come on guys, has nobody ever managed to get the application switch button working under Wine? 

I don't need to be able to switch applications or anything I just wanna be able to keybind the button and use it like I have always done on windows.

---

### Post by NightMKoder on 2009-06-15
Wait for XInput 2. Then a lot of these problems will be solved. For now, wine doesn't understand the keystroke and hence doesn't register it.

---

