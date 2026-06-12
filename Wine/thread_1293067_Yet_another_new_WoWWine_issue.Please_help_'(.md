---
title: "Yet another new WoW/Wine issue.Please help :'("
date: 2009-10-16
forum: Wine
---

### Post by m0rbidpercepti0ns on 2009-10-16
Ok so...back in Feisty days i was running WoW on Wine so flawlessly that i wondered if i could run multiple accounts in the main cities with one PC>..it was that good,my FPS was SKYHIGH,and my latency were bottom of the barrel low. Ive recently had an XP problem *big suprise there* and have come back to Ubuntu 9.04. Im a very avid WoW Raider...installing WoW on this distro was hard,with plenty of problems,everything from greyed out agree buttons to just..not running,not installing,loader errors..and searching the forums,and google was defenitly able to fix everything with a bit of work,however..i cant seem to raise my FPS.Im usualy at 3-5 FPS. Ive gotten as high as 20,but only in flight on my mount,where theres not much to render. I believe the issue resides in how its handling the video somehow? Im not sure.Ive added the registry key for openGL,and i run WoW in openGL,i use an Nvidia 6200OC. and im using the newest WINE. 1.30 Wine was ridiculiously horrible. Updating to 1.31 defenitly helped..I run WoW as Windows XP,being as changing the WIndows OS doesnt seem to help much.By this point i would do ANYTHING to have someone help me fix this. i dont want to go back to Windows...and Ubuntu wont load my windows install disk anyhow, icant run it from wine,or in ubuntu,and switching my boot process to CD drive doesnt do it...it still just boots my Ubuntu splash. But thats another post entirely. All help and ideas are GREATLY appreciated.

---

### Post by beastrace91 on 2009-10-16
Hey There,

I know the last two Wine versions (.30 and .31) suffered from some regressions in the 3D department. Have you tried running it under [1.1.29](http://wine.budgetdedicated.com/archive/index.html)?

Also what nVidia driver are you running? (And odds are alot of the other issues you had have more to due with WoW updates in recent years than regressions in the Wine project THAT much)

~Jeff

---

### Post by m0rbidpercepti0ns on 2009-10-17
Im using Nvidia version 180,but ive tried both of the other two that Ubuntu has listed for restricted drivers. Could you possibly direct me on how to downgrade my Wine? I cant seem to find it anywhere. WineHQ only appears to make one previous install available.Also..im not sure its the WoW updates,because Blizzard supports people who use Linux..ive seen it in the WoW forums,they do their best to help people...i dont know why they dont just develop it for all. Thank you kindly for you help,by the way:)

---

### Post by hikaricore on 2009-10-17
[http://wine.budgetdedicated.com/archive/index.html](http://wine.budgetdedicated.com/archive/index.html)

Blizzard helping linux users?  I love to see that..

---

### Post by m0rbidpercepti0ns on 2009-10-22
Ive downgraded to WINE 1.1.29 and its made it so that occasionally my FPS will go up randomly,for a few moments,before dropping back down. Should i keep trying to downgrade until i find one that works? This problem is becoming my ultimate frustration. lol. Everyone else seems to run WoW fine on Jaunty with Wine,even 1.1.30 and 31:P by this point id pay for successful help:P

---

### Post by hikaricore on 2009-10-22
Have you disabled desktop effects and tested with the screensaver set to off?
These things often impact resource heavy applications and games.

---

### Post by joeelmex on 2009-10-22
I run Wow fine with Ubuntu Jaunty I did compile the latest kernel.  I also played it with Cedega but now use Wine because my extra mouse buttons work without a glitch in Wine.

---

### Post by m0rbidpercepti0ns on 2009-10-22
Yeah,i have my desktop effects set to none,and no enabled screensaver,any ideas?

---

