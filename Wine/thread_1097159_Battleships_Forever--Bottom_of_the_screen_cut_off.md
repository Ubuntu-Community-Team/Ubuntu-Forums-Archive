---
title: "Battleships Forever--Bottom of the screen cut off"
date: 2009-03-15
forum: Wine
---

### Post by GNU Gnerd on 2009-03-15
Greetings, all.

I'm trying to get Battleships Forever (a build-your-own-ship space combat game) to work under Wine.  Everything runs just fine (you can play the game, move everything on the screen, etc.)...except that the bottom part of the screen is just black, and the amount of blackness depends on which screen I'm on:

[IMG]http://i208.photobucket.com/albums/bb176/psychictheurge10/BF.png[/IMG]

The strange part is that the mouse is in the same relative location to my desktop, even though the screen is shifted--if I have my mouse outside of the window lined up with the "Exit" button, when I move it into the window it comes in lined up with the "Custom Game" button.  This makes it difficult to click and move anything, since I have to try to guess where the mouse actually is when the cursor is over a button.

I have a basic Wine install (no custom changes, registry hacks, etc.) and an NVidia Quadro graphics card; I doubt it's the graphics card, since on my Windows partition the screen is placed correctly.  I'm running Hardy on a Lenovo T61 laptop, if that helps.

Any ideas?

---

### Post by Meow27 on 2009-03-15
i remember having this problem..

are you playing windowed or full screen.

i never got around it.. i recommend you playing it on windows if you dual boot, cause itl run slower on Wine

---

### Post by GNU Gnerd on 2009-03-16
> **Meow27 said:**
> i remember having this problem..

are you playing windowed or full screen.

Windowed; it won't let me go full screen, as the "maximize" button is grayed out.

> i never got around it.. i recommend you playing it on windows if you dual boot, cause itl run slower on Wine

So there's no real solution, then?  I could run it on Windows, but I only really use that partition for schoolwork (there are a few programs I need that won't run under Wine) and I was hoping to keep all my games on the Ubuntu partition....

---

### Post by Meow27 on 2009-03-16
whoa. i do the opposite LOL i use ubuntu for schoolwork and windows for games :P

keep bumping ur post until you find ur answer :3

---

### Post by GNU Gnerd on 2009-03-16
> **Meow27 said:**
> whoa. i do the opposite LOL i use ubuntu for schoolwork and windows for games :P

keep bumping ur post until you find ur answer :3

Well, I use Windows for just two programs for physics; 99% of my computer use is Ubuntu, and if those programs would run in Wine I wouldn't even be dual-booting.


Anyone else have an idea of how I might fix the problem?

---

### Post by DragonProfighter on 2009-03-16
hi i had the same problem and i manage to find out how to get it so its play able what i did was **set wine to Emulate a virtual desktop and set the desktop size to 1032x810** don't try full screen it'll make the game crash hope this helps

---

### Post by GNU Gnerd on 2009-03-17
> **DragonProfighter said:**
> hi i had the same problem and i manage to find out how to get it so its play able what i did was **set wine to Emulate a virtual desktop and set the desktop size to 1032x810** don't try full screen it'll make the game crash hope this helps

It's working!  Well, mostly.  There's still a bit of a mismatch, but now I can at least reach most of the buttons on all the screens.  I didn't even think to set it to emulate something besides my full screen size.  I'll fiddle around with it and see if I can get the last half-inch of blackness to go away.

Thanks again!

---

