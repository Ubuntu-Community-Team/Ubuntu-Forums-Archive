---
title: "Poor framerate in games"
date: 2009-01-25
forum: Wine
---

### Post by mr_x408 on 2009-01-25
Hey guys i have a hp laptop running ubuntu and i was wondering why the framerate in most of my games that i run through wine is rather slow, for instance in wow when im in a large area i have got a whopping 6fps sometimes. i was wondering if there is anything i can do to improve this. i have already installed directx9.0c through wine and it helped a bit.
here's my computer specs:
i have a 32mb NVIDIA GeForce 7150M graphics card
1 gig of ram
1.7 GHz AMD Athlon 64 X2 

it the only thing i can do to improve this is buy more ram?

---

### Post by Meow27 on 2009-01-25
i think the real issue is with your CPU

though in a situation where you don't have a custom built computer, I think its best to buy a new one with more CPU power

1.7GHz is rather low (its probably bogged down to 1.2 GHz preformance in Wine)

edit--- the gpu only has 32 mb? that sounds pretty low in today's standards :/

---

### Post by mr_x408 on 2009-01-25
hrmm thats really unfortunate because its only half a year old and im outof money -_-

---

### Post by SR_ELPIRATA on 2009-01-26
Have u checked in the bios? Many computers allow the user to manually allocate the ammount of shared memory they want to use with their video cards. Some manufacuters/chipsets may have a max limit, perhaps 256? but most probably you will be able to allocate more memory within the bios.

ELP

---

### Post by Shaythong on 2009-01-27
I have the 7150M graphics card and in the BIOS the max shared memory that I can allocate is 128 MB. ;)

---

### Post by shae on 2009-01-28
You should also try the opengl renderer with WoW.

One thing to consider is that Wine often CPU-bottlenecks games that otherwise are bottlenecked by other parts of the system because it has to use the CPU to translate windows calls into their equivalent linux ones.

Furthermore increasing the memory allocated to your graphics card in BIOS might also help you get it running better.

I suggest you check out WoW's pages in the AppDB at winehq for more information about running the game well.

---

