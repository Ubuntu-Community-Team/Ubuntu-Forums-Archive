---
title: "Wine:Fonts missing in google talk"
date: 2009-11-28
forum: Wine
---

### Post by futureal2032 on 2009-11-28
hi,
i am using Ubuntu 9.10 Karmic

using wine 1.2

i installed google talk

google talk runs fine ..but there are no fonts on gtalk window..

i mean i don't see any kind of text when i open Google talk..

so i typed my user name (which gets types by the way and i can see its text)

and i logged in by typing password and pressing Enter

it connects fine ...but again there is no text shown..no menus no buddy names nothing.

other programs i have installed on wine ..like yahoo messenger , winamp etc are running fine and show text...only gtalk does not show any text..

can anyone pls help?

i have tried copying all fonts from windows xp to .wine/c:/windows/Fonts folder

but only gtalk does not show any text

---

### Post by beastrace91 on 2009-11-28
Have you tried using [Winetricks](http://wiki.winehq.org/winetricks) to install all "core fonts" from Winblows? If not give it a go and see if it helps.

Regards,
~Jeff

---

### Post by futureal2032 on 2009-11-29
> **beastrace91 said:**
> Have you tried using [Winetricks](http://wiki.winehq.org/winetricks) to install all "core fonts" from Winblows? If not give it a go and see if it helps.

Regards,
~Jeff

hi,
i installed winetricks..

i executed this command also "sh winetricks" 
and tried to install packages like core fonts, runtime libraries etc..

problem is it does not install 90% of the things i selected giving one or other errors..

and it did not solve my problem

---

### Post by Loadus on 2010-09-29
> **futureal2032 said:**
> hi,
i installed winetricks..

i executed this command also "sh winetricks" 
and tried to install packages like core fonts, runtime libraries etc..

problem is it does not install 90% of the things i selected giving one or other errors..

and it did not solve my problem

On the latest WINE (1.3.3), you can use winetricks to install Richedit 3.0 and ie6. Richedit will give you the missing text from the Gtalk dialogue and ie6 will enable the chat window's functions. ^^

---

