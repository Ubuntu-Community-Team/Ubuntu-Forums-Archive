---
title: "Warcraft 3 problems since upgrade to Ubuntu 9.04"
date: 2009-04-13
forum: Wine
---

### Post by shaolinmilk on 2009-04-13
When I open my Frozen Throne.exe file with the latest version of wine(1.1.19), it opens at first and changes the resolution to the one that's in the game and then after that, the screen just goes black and stays there forever. I could still move my mouse, but I cannot do anything else besides that! So then I have to restart my computer because I cannot do anything. 

What is the problem? Does anyone know?

---

### Post by Mokoma on 2009-04-13
> **shaolinmilk said:**
> When I open my Frozen Throne.exe file with the latest version of wine(1.1.19), it opens at first and changes the resolution to the one that's in the game and then after that, the screen just goes black and stays there forever. I could still move my mouse, but I cannot do anything else besides that! So then I have to restart my computer because I cannot do anything. 

What is the problem? Does anyone know?

did you nuke the movies file already?

---

### Post by shaolinmilk on 2009-04-13
Yes I have. I can't seem to uninstall it. Maybe something got corrupted when I upgraded? Does anyone else have a problem like this?

---

### Post by NightMKoder on 2009-04-13
If it worked in intrepid and doesn't work in jaunty, the most likely culprit is video drivers. What is your video card/driver?

---

### Post by shaolinmilk on 2009-04-14
I have an nvidia geforce 6200 and the driver that I currently have installed is 180.25.

Also, if I don't put -opengl, when I open up Warcraft, it says "Warcraft III was unable to initialize DirectX. Please ensure you have DirectX 8.1 or newer installed...". This has never ever happened to me before.

---

### Post by shaolinmilk on 2009-04-22
Can anyone help me? It's been a week now. :(

---

### Post by nwadams on 2009-04-22
if you don't solve it in a week i'll be attempting to do the same thing as you...We will see.

---

### Post by Kidfork on 2009-04-22
> **shaolinmilk said:**
> I have an nvidia geforce 6200 and the driver that I currently have installed is 180.25.

Also, if I don't put -opengl, when I open up Warcraft, it says "Warcraft III was unable to initialize DirectX. Please ensure you have DirectX 8.1 or newer installed...". This has never ever happened to me before.

How did you install the 180 Driver, i tried from the Nvidia Site and it borked my system.

---

### Post by Uzi304 on 2009-04-22
I'm having the same problem. I start Warcraft 3 and it just has a blank screen. I tried disabling Compiz and it didn't do much better. I can hear sound from the movie clip but I can't see anything and I have to do a hard reset.

---

### Post by shaolinmilk on 2009-04-25
> **Kidfork said:**
> How did you install the 180 Driver, i tried from the Nvidia Site and it borked my system.
There was a tutorial somewhere on this forum. Look around.

I still can't fix it! It's just a blank screen and I could move my my around and that's the only thing that's visible!

---

### Post by Uzi304 on 2009-04-29
Ok try this, it kinda helped me. Go into your Wine config and click on the graphics tab and check the box that says emulate a virtual desktop and you can make the size what you want. That might work, good luck

---

### Post by hotweiss on 2009-04-29
The problem that I have is that the bottom panel is still visible when virtual desktop is enabled.

---

### Post by shaolinmilk on 2009-04-30
> **Uzi304 said:**
> Ok try this, it kinda helped me. Go into your Wine config and click on the graphics tab and check the box that says emulate a virtual desktop and you can make the size what you want. That might work, good luck
I have tried that already and it still does not work.

---

### Post by Maggush on 2009-05-05
I have the same problem :(:(

---

### Post by cjminton on 2009-07-17
make sure you change the name of the C:\Program Files\Warcraft\Movies\ folder

if you have already done that and your still having troubles then try to use the registry editor

open a terminal, enter the following:

```
wine regedit
```

ok now the windows registry editor should have popped up, navigate your way to 

HKEY_CURRENT_USER/Software/Blizzard Entertainment/Warcraft III/Video

okay now after you click Video folder go through the settings to the right and when you configure one by double clicking them **make sure you select the decimal input. **

the ones i set are 'refreshrate' i have to set mine to 60, next i change resheight and reswidth to whatever my monitors default specs are. 

when your done just X out and then try running the game again.

hope this helps.

---

