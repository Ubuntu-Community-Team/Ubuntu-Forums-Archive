---
title: "keyboardlayout"
date: 2009-09-18
forum: The Cafe
---

### Post by lolleprof on 2009-09-18
Sorry all but I have a problem!
Tried to get a swedish layout in 9.04 but it dont work. (just look at this text) Ok, we do have a few different signs and letters but in the setup there is a swdish layout. does not work for me though. Laptop Acer. Only geting Danish letters and the specific signs like at and so on will only be by experimet... Is there nybody out there who can guide me? 8.04 worked just fine. Will concider installing 8.04 studion instead othherwise, do handel a bit of my own music... Very good and low latency.
Hey! Love you all!

---

### Post by ChrT on 2009-09-18
works for me

(If you're using gnome: System->Preferences->Keyboard->Layout->Add->select Sweden, then switch to swedish layout using the panel applet)

åöøäðßþ

:)

---

### Post by lolleprof on 2009-09-20
As much as I appreciate your attempt, witch absolutely ought to be the correct way to do this, I fail to get it right. It shows on the layoutaplet a semicorrect (if there is such a word) set of keys that looks right but pressing them, with or without any combo, only gives signs not used in swedish. It's not the keyboard itself (Acer Travelmate 2410) it works allright in Winxp, using it now not to get too pissed writing this, so there must be another issue. The entire Ubuntu runs slower than Windows and tha is not my previous experience. There may be a woops here...Will take a look to se if I by misstake put an 64-bit version in this x86 machine... (The AMD-machine is right beside me... Naah! that can't be the reason for this? 
Great thanks anyway!
Gonna get this thing working, one way or another.

---

### Post by lolleprof on 2009-09-24
Err.. I'm closing this now. Got my native letters working. 
Have you any idea what a numlock can do...? How embarresing!
Thank you!

---

### Post by lolleprof on 2009-09-24
I'm ba-ack! Had it working for a while, then added ubuntustudio. Now the keyboard has gone back to its silly acting again. Very boring issue this. It's never too late to give up... If I find a way or a remedy to this what seem to be a very singular problem, I will let you all know.
See You!

---

### Post by Bölvaður on 2009-09-24
Check which layout you are using and change the corresponding file in /usr/share/X11/xkb/symbols

I guess this is the command you are looking for to edit it manually

```
gksu gedit /usr/share/X11/xkb/symbols/se
```

You can try add a new type of layout or change one that already exists to only show A for every button, and then change it manually back to what it is actually supposed to be. There might be something special about your keyboard which works in a special way, this is how you can change the layout ANY way you want.

---

### Post by lolleprof on 2009-09-24
I'm most grateful! Very nice! I had that thougt for a while but concluded there had to be an easier way. I will look into that in a moment and try to understand though. I really do appreciate your efforts to get a noob up and running!
So happens, I downloaded three files to support swedish, the module had the curtesy to ask if I wanted that, so I did. Don't know if that was really needed since it worked earlier. However, did so, added layout and... no change. :-( Then, by misstake, I deleted the default keyboard (Italian) on the list, of four possible layouts, and.. WHOOPS! The aplet seem to work like a bootlist :-) ; What's on top goes first! With only the swedish keyboard on the list I'm back in business. (didn't even find the @ on any key elsewise and you can understand what trouble that is...)
Anyway, up and running now. 
Many thanks again!
(Now it's time to get a peak on the gamingsection. Flightsimfan...)

---

