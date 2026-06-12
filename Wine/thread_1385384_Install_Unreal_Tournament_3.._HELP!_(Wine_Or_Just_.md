---
title: "Install Unreal Tournament 3.. HELP!? (Wine Or Just Plain Old Linux Install)"
date: 2010-01-19
forum: Wine
---

### Post by master620 on 2010-01-19
ok, i have been in several forums with titles stating that they need help with this and yet no one has once said anything constructive at all! i'm making this in hope that SOMEONE can help me with this annoying problem.. 

there doesn't seem to be any way to install using just plain old linux (running Karmic [9.10]). i've installed it using Wine, yet it just shows the splash screen, then shows a very small window which disappears after about 1 minute of nothingness. i looked around and wine's website shows that they support it and that it works nearly flawlessly! BUT i can not seem to get it to work.

also they say that you need two registry keys entered into the Wine Registry. although they have a link that shows where you should put the keys, i see NOTHING even remotely like that in my Wine's registry... its supposed to go under:

HKEY_CURRENT_USER => Software => Wine => Direct3D
HKEY_CURRENT_USER => Software => Wine => DirectInput

Yet i have no Direct3D or DirectInput subfolders, only thing in my "Wine" folder there is Debug, Drivers, Fonts, MSHTML, Temporary System Parameters, and WineDbg... 

so anyone have ANY ideas on how i am supposed to do any of this?? i'd really like to start playing this again... i've had it since the day it came out, and this is the only time i've had any problems with it..

---

### Post by beastrace91 on 2010-01-19
What Wine version are you attempting to install under?

Also - if you really want to play UT3 under Linux, I would *strongly* recommend paying for [Cedega](http://www.cedega.com/) - as even if you get UT3 working under Wine the performance is terrible at best.

EDIT: Also, regarding the keys - simply add any missing subfolders/keys if they do not exist.

~Jeff

---

