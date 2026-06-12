---
title: "Wine, a new computer, fresh Ubunt install, and Eve Online."
date: 2010-07-18
forum: Wine
---

### Post by Bampfsnap on 2010-07-18
So, I have an ATI HD4200 and teh ubuntu says that it can see this card just fine, but when Im in Eve my GFX looks like crap and i have bad FPS.


Im not really good at using computers, but I wrote in the command lines to use winetricks and get the fonts with it so I could get past the startup screen.

Now I have this problem. the planet is supposed to be rich in colors and that blob on the rigfht is a really detailed spacestation thing when using a Macbook.

the next screenshot is in a station which should be full of lights and moving objects, etc.

what am I missing or forgetting? I have spent 10+ hours looking through google on how to get eve online to run. it is now set as gold by wine, so is it just some drivers for video I have to install in wine?

---

### Post by asdfoo on 2010-07-18
you probably need to install the latest fglrx drivers for your card

---

### Post by Bampfsnap on 2010-07-19
okay I did that twice now and it does work for visual, but now it crashes the whole computer.,

the first time, the first pic looked proper, and then the avatar models in the next page still had the look of black and white polygon faces when selecting them for some reason. it was all grayscale.

Then trying to get in to the second pic, the station, it froze the whole computer, wine, eve client, and ubuntu.

I reinstalled all of ubuntu two days ago, and went through it again, this time I installed drivers then wine, and then didnt install anything else with winetricks but the core fonts. then I installed eve.

the first screen looks proper, the second screen with the avatar faces looks proper, but still, trying to get into the game it freezes wine, eve client, and ubuntu. i have to press reset. lucky I opted for a case that has that option, since everyone thinks linux doesnt crash, but still, I cant play.

---

### Post by ronnielsen1 on 2010-07-19
If you're trying to run windows applications in linux using wine ALWAYS google [COLOR="DarkSlateGray"]winehq softwareyouwanttorun[/COLOR]

[http://appdb.winehq.org/objectManager.php?sClass=version&iId=9971](http://appdb.winehq.org/objectManager.php?sClass=version&iId=9971)

It seems you have to manually edit some fileswinehq softwareyouwanttorun

---

### Post by Bampfsnap on 2010-07-19
wow thanks. I set it to open gl and no more total OS crashes, but then when Im typing here for instance, or when I mouse over a different tab in firefox while the game is running, it flickers and I get to see the background of the desktop of wine and the splash screen of the game.. and I cant successfully jump without crashing it.

---

### Post by asdfoo on 2010-07-20
> **Bampfsnap said:**
> wow thanks. I set it to open gl and no more total OS crashes, but then when Im typing here for instance, or when I mouse over a different tab in firefox while the game is running, it flickers and I get to see the background of the desktop of wine and the splash screen of the game.. and I cant successfully jump without crashing it.

total OS crash is because ATI/AMD release bad quality driver, probably same for flickering - unfortunately.

you can try a newer version, eg catalyst 10.7 and hope the bug is gone.

---

