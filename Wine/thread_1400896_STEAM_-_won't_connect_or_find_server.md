---
title: "STEAM - won't connect or find server"
date: 2010-02-07
forum: Wine
---

### Post by savaan on 2010-02-07
I'm trying to play CS 1.6 and TFC through WINE. My game will start up fine, but when it gets to the "establishing conntection" part, it crashes and goes back to the main steam window.

---

### Post by beastrace91 on 2010-02-07
Wine version?

~Jeff

---

### Post by savaan on 2010-02-07
WINE 1.2, sorry. Had to look that up

---

### Post by Soulcage on 2010-02-08
There is no version 1.2 just yet instead type wine --version into a terminal. Also last I checked all the gold source games (hl cs tfc opf blshift) would crash almost all the time. Run steam through a terminal to find out for sure. "cd ~/.wine/drive_c/Program\ Files/Steam && wine Steam.exe" then launch the game you may want to run the game in windowed mode by adding -windowed to the advanced options inside steam. Right click the game then click properties then adv options or w/e it's called.

---

### Post by savaan on 2010-02-08
My WINE version is 1.1.31. Thanks, I'm still learning my way around Linux :) 
Launching from the terminal did the exact same thing as launching from my WINE menu. The game starts up just fine and I click on FIND SERVERS or CREATE SERVER. It goes through 'establishing connection" and a few other progress bars, then just crashes right back to my desktop/main STEAM window. I had this problem in Windows when my video settings were too high for the card I had. I simply reset the video lower and problem solved. Doesn't seem to be the case here though


Those commands threw off a looong series of messages in terminal...
```
fixme:mshtml:DispatchEx_GetDispID Unsupported grfdex 8
fixme:mshtml:DispatchEx_GetDispID Unsupported grfdex 8
fixme:mshtml:DispatchEx_GetDispID Unsupported grfdex 8
fixme:mshtml:DispatchEx_GetDispID Unsupported grfdex 8
fixme:mshtml:DispatchEx_GetDispID Unsupported grfdex 8
fixme:mshtml:DispatchEx_GetDispID Unsupported grfdex 8
fixme:mshtml:DispatchEx_GetDispID Unsupported grfdex 8
fixme:mshtml:DispatchEx_GetDispID Unsupported grfdex 8
fixme:mshtml:DispatchEx_GetDispID Unsupported grfdex 8
fixme:mshtml:DispatchEx_GetDispID Unsupported grfdex 8
fixme:mshtml:DispatchEx_GetDispID Unsupported grfdex 8
fixme:mshtml:DispatchEx_GetDispID Unsupported grfdex 8
fixme:mshtml:DispatchEx_GetDispID Unsupported grfdex 8
fixme:mshtml:DispatchEx_GetDispID Unsupported grfdex 8
fixme:mshtml:DispatchEx_GetDispID Unsupported grfdex 8
fixme:mshtml:DispatchEx_GetDispID Unsupported grfdex 8
fixme:mshtml:DispatchEx_GetDispID Unsupported grfdex 8
fixme:mshtml:DispatchEx_GetDispID Unsupported grfdex 8
fixme:mshtml:DispatchEx_GetDispID Unsupported grfdex 8
fixme:mshtml:DispatchEx_GetDispID Unsupported grfdex 8
fixme:mshtml:DispatchEx_GetDispID Unsupported grfdex 8
fixme:mshtml:DispatchEx_GetDispID Unsupported grfdex 8
fixme:mshtml:DispatchEx_GetDispID Unsupported grfdex 8
fixme:mshtml:DispatchEx_GetDispID Unsupported grfdex 8
fixme:mshtml:DispatchEx_GetDispID Unsupported grfdex 8
fixme:mshtml:DispatchEx_GetDispID Unsupported grfdex 8
fixme:mshtml:DispatchEx_GetDispID Unsupported grfdex 8
fixme:mshtml:DispatchEx_GetDispID Unsupported grfdex 8
fixme:mshtml:DispatchEx_GetDispID Unsupported grfdex 8
fixme:mshtml:DispatchEx_GetDispID Unsupported grfdex 8
fixme:mshtml:DispatchEx_GetDispID Unsupported grfdex 8
fixme:mshtml:DispatchEx_GetDispID Unsupported grfdex 8
fixme:mshtml:DispatchEx_GetDispID Unsupported grfdex 8
fixme:mshtml:DispatchEx_GetDispID Unsupported grfdex 8
fixme:mshtml:DispatchEx_GetDispID Unsupported grfdex 8
fixme:mshtml:DispatchEx_GetDispID Unsupported grfdex 8
fixme:mshtml:DispatchEx_GetDispID Unsupported grfdex 8
fixme:mshtml:DispatchEx_GetDispID Unsupported grfdex 8
fixme:mshtml:DispatchEx_GetDispID Unsupported grfdex 8
fixme:mshtml:DispatchEx_GetDispID Unsupported grfdex 8
fixme:mshtml:DispatchEx_GetDispID Unsupported grfdex 8
fixme:mshtml:DispatchEx_GetDispID Unsupported grfdex 8
fixme:mshtml:DispatchEx_GetDispID Unsupported grfdex 8
fixme:mshtml:DispatchEx_GetDispID Unsupported grfdex 8
fixme:mshtml:DispatchEx_GetDispID Unsupported grfdex 8
fixme:mshtml:DispatchEx_GetDispID Unsupported grfdex 8
fixme:mshtml:DispatchEx_GetDispID Unsupported grfdex 8
fixme:mshtml:DispatchEx_GetDispID Unsupported grfdex 8
fixme:mshtml:DispatchEx_GetDispID Unsupported grfdex 8
fixme:mshtml:DispatchEx_GetDispID Unsupported grfdex 8
fixme:mshtml:DispatchEx_GetDispID Unsupported grfdex 8
fixme:mshtml:DispatchEx_GetDispID Unsupported grfdex 8
fixme:mshtml:DispatchEx_GetDispID Unsupported grfdex 8
fixme:shdocvw:InPlaceActiveObject_TranslateAccelerator (0x343a158)->(0x32c8fc)
fixme:shdocvw:InPlaceActiveObject_TranslateAccelerator (0x343a158)->(0x32be48)
fixme:shdocvw:InPlaceActiveObject_TranslateAccelerator (0x343a158)->(0x32c8fc)
fixme:shdocvw:InPlaceActiveObject_TranslateAccelerator (0x343a158)->(0x32c8fc)
fixme:shdocvw:InPlaceActiveObject_TranslateAccelerator (0x343a158)->(0x32c8fc)
fixme:shdocvw:InPlaceActiveObject_TranslateAccelerator (0x343a158)->(0x32c8fc)
fixme:shdocvw:InPlaceActiveObject_TranslateAccelerator (0x343a158)->(0x32c8fc)
fixme:shdocvw:InPlaceActiveObject_TranslateAccelerator (0x343a158)->(0x32c8fc)
fixme:shdocvw:InPlaceActiveObject_TranslateAccelerator (0x343a158)->(0x32c8fc)
fixme:shdocvw:InPlaceActiveObject_TranslateAccelerator (0x343a158)->(0x32c8fc)
fixme:shdocvw:InPlaceActiveObject_TranslateAccelerator (0x343a158)->(0x32c8fc)
fixme:shdocvw:InPlaceActiveObject_TranslateAccelerator (0x343a158)->(0x32c8fc)
fixme:shdocvw:InPlaceActiveObject_TranslateAccelerator (0x343a158)->(0x32c8fc)
fixme:mshtml:DispatchEx_GetDispID Unsupported grfdex 8
fixme:mshtml:DispatchEx_GetDispID Unsupported grfdex 8
fixme:mshtml:DispatchEx_GetDispID Unsupported grfdex 8
fixme:mshtml:DispatchEx_GetDispID Unsupported grfdex 8
fixme:mshtml:DispatchEx_GetDispID Unsupported grfdex 8
fixme:mshtml:DispatchEx_GetDispID Unsupported grfdex 8
fixme:shdocvw:InPlaceActiveObject_TranslateAccelerator (0x343a158)->(0x32c8fc)
fixme:mshtml:DispatchEx_GetDispID Unsupported grfdex 8
fixme:mshtml:DispatchEx_GetDispID Unsupported grfdex 8
fixme:mshtml:DispatchEx_GetDispID Unsupported grfdex 8
fixme:mshtml:DispatchEx_GetDispID Unsupported grfdex 8
fixme:mshtml:DispatchEx_GetDispID Unsupported grfdex 8
fixme:mshtml:DispatchEx_GetDispID Unsupported grfdex 8
fixme:shdocvw:InPlaceActiveObject_TranslateAccelerator (0x343a158)->(0x32c8fc)
fixme:mshtml:DispatchEx_GetDispID Unsupported grfdex 8
fixme:mshtml:DispatchEx_GetDispID Unsupported grfdex 8
fixme:mshtml:DispatchEx_GetDispID Unsupported grfdex 8
fixme:mshtml:DispatchEx_GetDispID Unsupported grfdex 8
fixme:mshtml:DispatchEx_GetDispID Unsupported grfdex 8
fixme:mshtml:DispatchEx_GetDispID Unsupported grfdex 8
fixme:shdocvw:InPlaceActiveObject_TranslateAccelerator (0x343a158)->(0x32c8fc)
fixme:mshtml:DispatchEx_GetDispID Unsupported grfdex 8
fixme:mshtml:DispatchEx_GetDispID Unsupported grfdex 8
fixme:mshtml:DispatchEx_GetDispID Unsupported grfdex 8
fixme:mshtml:DispatchEx_GetDispID Unsupported grfdex 8
fixme:shdocvw:InPlaceActiveObject_TranslateAccelerator (0x343a158)->(0x32c8fc)
fixme:mshtml:DispatchEx_GetDispID Unsupported grfdex 8
fixme:mshtml:DispatchEx_GetDispID Unsupported grfdex 8
fixme:mshtml:DispatchEx_GetDispID Unsupported grfdex 8
fixme:mshtml:DispatchEx_GetDispID Unsupported grfdex 8
fixme:mshtml:DispatchEx_GetDispID Unsupported grfdex 8
fixme:mshtml:DispatchEx_GetDispID Unsupported grfdex 8
fixme:shdocvw:InPlaceActiveObject_TranslateAccelerator (0x343a158)->(0x32c8fc)
fixme:shdocvw:InPlaceActiveObject_TranslateAccelerator (0x343a158)->(0x32c8fc)
fixme:mshtml:DispatchEx_GetDispID Unsupported grfdex 8
fixme:mshtml:DispatchEx_GetDispID Unsupported grfdex 8
fixme:mshtml:DispatchEx_GetDispID Unsupported grfdex 8
fixme:mshtml:DispatchEx_GetDispID Unsupported grfdex 8
fixme:mshtml:DispatchEx_GetDispID Unsupported grfdex 8
fixme:mshtml:DispatchEx_GetDispID Unsupported grfdex 8
fixme:shdocvw:InPlaceActiveObject_TranslateAccelerator (0x343a158)->(0x32c8fc)
fixme:shdocvw:InPlaceActiveObject_TranslateAccelerator (0x343a158)->(0x32c8fc)
fixme:shdocvw:InPlaceActiveObject_TranslateAccelerator (0x343a158)->(0x32c8fc)
fixme:mshtml:DispatchEx_GetDispID Unsupported grfdex 8
fixme:mshtml:DispatchEx_GetDispID Unsupported grfdex 8
fixme:mshtml:DispatchEx_GetDispID Unsupported grfdex 8
fixme:mshtml:DispatchEx_GetDispID Unsupported grfdex 8
fixme:shdocvw:InPlaceActiveObject_TranslateAccelerator (0x343a158)->(0x32c8fc)
fixme:shdocvw:InPlaceActiveObject_TranslateAccelerator (0x343a158)->(0x32c8fc)
fixme:shdocvw:InPlaceActiveObject_TranslateAccelerator (0x343a158)->(0x32c8fc)
fixme:shdocvw:InPlaceActiveObject_TranslateAccelerator (0x343a158)->(0x32c8fc)
fixme:shdocvw:InPlaceActiveObject_TranslateAccelerator (0x343a158)->(0x32c8fc)
fixme:mshtml:DispatchEx_GetDispID Unsupported grfdex 8
fixme:mshtml:DispatchEx_GetDispID Unsupported grfdex 8
fixme:mshtml:DispatchEx_GetDispID Unsupported grfdex 8
fixme:mshtml:DispatchEx_GetDispID Unsupported grfdex 8
fixme:mshtml:DispatchEx_GetDispID Unsupported grfdex 8
fixme:mshtml:DispatchEx_GetDispID Unsupported grfdex 8
fixme:shdocvw:InPlaceActiveObject_TranslateAccelerator (0x343a158)->(0x32c8fc)
fixme:mshtml:DispatchEx_GetDispID Unsupported grfdex 8
fixme:mshtml:DispatchEx_GetDispID Unsupported grfdex 8
fixme:mshtml:DispatchEx_GetDispID Unsupported grfdex 8
fixme:mshtml:DispatchEx_GetDispID Unsupported grfdex 8
fixme:mshtml:DispatchEx_GetDispID Unsupported grfdex 8
fixme:mshtml:DispatchEx_GetDispID Unsupported grfdex 8
fixme:shdocvw:InPlaceActiveObject_TranslateAccelerator (0x343a158)->(0x32c8fc)
fixme:shdocvw:InPlaceActiveObject_TranslateAccelerator (0x343a158)->(0x32c8fc)
fixme:mshtml:DispatchEx_GetDispID Unsupported grfdex 8
fixme:mshtml:DispatchEx_GetDispID Unsupported grfdex 8
fixme:mshtml:DispatchEx_GetDispID Unsupported grfdex 8
fixme:mshtml:DispatchEx_GetDispID Unsupported grfdex 8
fixme:mshtml:DispatchEx_GetDispID Unsupported grfdex 8
fixme:mshtml:DispatchEx_GetDispID Unsupported grfdex 8
fixme:shdocvw:InPlaceActiveObject_TranslateAccelerator (0x343a158)->(0x32c8fc)
fixme:mshtml:DispatchEx_GetDispID Unsupported grfdex 8
fixme:mshtml:DispatchEx_GetDispID Unsupported grfdex 8
fixme:mshtml:DispatchEx_GetDispID Unsupported grfdex 8
fixme:mshtml:DispatchEx_GetDispID Unsupported grfdex 8
fixme:mshtml:DispatchEx_GetDispID Unsupported grfdex 8
fixme:mshtml:DispatchEx_GetDispID Unsupported grfdex 8
fixme:mshtml:DispatchEx_GetDispID Unsupported grfdex 8
fixme:mshtml:DispatchEx_GetDispID Unsupported grfdex 8
fixme:mshtml:DispatchEx_GetDispID Unsupported grfdex 8
fixme:mshtml:DispatchEx_GetDispID Unsupported grfdex 8
fixme:mshtml:DispatchEx_GetDispID Unsupported grfdex 8
fixme:mshtml:DispatchEx_GetDispID Unsupported grfdex 8
fixme:mshtml:DispatchEx_GetDispID Unsupported grfdex 8
fixme:mshtml:DispatchEx_GetDispID Unsupported grfdex 8
fixme:mshtml:DispatchEx_GetDispID Unsupported grfdex 8
fixme:mshtml:DispatchEx_GetDispID Unsupported grfdex 8
fixme:mshtml:DispatchEx_GetDispID Unsupported grfdex 8
fixme:mshtml:DispatchEx_GetDispID Unsupported grfdex 8
fixme:shdocvw:InPlaceActiveObject_TranslateAccelerator (0x343a158)->(0x32c8fc)
fixme:mshtml:DispatchEx_GetDispID Unsupported grfdex 8
fixme:mshtml:DispatchEx_GetDispID Unsupported grfdex 8
fixme:mshtml:DispatchEx_GetDispID Unsupported grfdex 8
fixme:mshtml:DispatchEx_GetDispID Unsupported grfdex 8
fixme:mshtml:DispatchEx_GetDispID Unsupported grfdex 8
fixme:mshtml:DispatchEx_GetDispID Unsupported grfdex 8
fixme:mshtml:DispatchEx_GetDispID Unsupported grfdex 8
fixme:mshtml:DispatchEx_GetDispID Unsupported grfdex 8
fixme:mshtml:DispatchEx_GetDispID Unsupported grfdex 8
fixme:mshtml:DispatchEx_GetDispID Unsupported grfdex 8
fixme:mshtml:DispatchEx_GetDispID Unsupported grfdex 8
fixme:mshtml:DispatchEx_GetDispID Unsupported grfdex 8
fixme:mshtml:DispatchEx_GetDispID Unsupported grfdex 8
fixme:mshtml:DispatchEx_GetDispID Unsupported grfdex 8
fixme:mshtml:DispatchEx_GetDispID Unsupported grfdex 8
fixme:mshtml:DispatchEx_GetDispID Unsupported grfdex 8
fixme:mshtml:DispatchEx_GetDispID Unsupported grfdex 8
fixme:mshtml:DispatchEx_GetDispID Unsupported grfdex 8
fixme:mshtml:DispatchEx_GetDispID Unsupported grfdex 8
fixme:mshtml:DispatchEx_GetDispID Unsupported grfdex 8
fixme:mshtml:DispatchEx_GetDispID Unsupported grfdex 8
fixme:mshtml:DispatchEx_GetDispID Unsupported grfdex 8
fixme:mshtml:DispatchEx_GetDispID Unsupported grfdex 8
fixme:mshtml:DispatchEx_GetDispID Unsupported grfdex 8
fixme:mshtml:DispatchEx_GetDispID Unsupported grfdex 8
fixme:mshtml:DispatchEx_GetDispID Unsupported grfdex 8
fixme:mshtml:DispatchEx_GetDispID Unsupported grfdex 8
fixme:mshtml:DispatchEx_GetDispID Unsupported grfdex 8
fixme:shdocvw:InPlaceActiveObject_TranslateAccelerator (0x343a158)->(0x32c8fc)
fixme:shdocvw:InPlaceActiveObject_TranslateAccelerator (0x343a158)->(0x32c8fc)
fixme:shdocvw:InPlaceActiveObject_TranslateAccelerator (0x343a158)->(0x32c8fc)
fixme:shdocvw:InPlaceActiveObject_TranslateAccelerator (0x343a158)->(0x32c8fc)
fixme:shdocvw:InPlaceActiveObject_TranslateAccelerator (0x343a158)->(0x32c8fc)
fixme:shdocvw:InPlaceActiveObject_TranslateAccelerator (0x343a158)->(0x32c8fc)
fixme:shdocvw:InPlaceActiveObject_TranslateAccelerator (0x343a158)->(0x32c8fc)
fixme:mshtml:DispatchEx_GetDispID Unsupported grfdex 8
fixme:mshtml:DispatchEx_GetDispID Unsupported grfdex 8
fixme:mshtml:DispatchEx_GetDispID Unsupported grfdex 8
fixme:mshtml:DispatchEx_GetDispID Unsupported grfdex 8
fixme:mshtml:DispatchEx_GetDispID Unsupported grfdex 8
fixme:mshtml:DispatchEx_GetDispID Unsupported grfdex 8
fixme:shdocvw:InPlaceActiveObject_TranslateAccelerator (0x343a158)->(0x32c8fc)
fixme:shdocvw:InPlaceActiveObject_TranslateAccelerator (0x343a158)->(0x32c8fc)
fixme:shdocvw:InPlaceActiveObject_TranslateAccelerator (0x343a158)->(0x32c8fc)
fixme:shdocvw:InPlaceActiveObject_TranslateAccelerator (0x343a158)->(0x32c8fc)
fixme:shdocvw:InPlaceActiveObject_TranslateAccelerator (0x343a158)->(0x32c8fc)
fixme:shdocvw:InPlaceActiveObject_TranslateAccelerator (0x343a158)->(0x32c8fc)
fixme:shdocvw:InPlaceActiveObject_TranslateAccelerator (0x343a158)->(0x32c8fc)
fixme:shdocvw:InPlaceActiveObject_TranslateAccelerator (0x343a158)->(0x32c8fc)
fixme:shdocvw:InPlaceActiveObject_TranslateAccelerator (0x343a158)->(0x32c8fc)
fixme:shdocvw:InPlaceActiveObject_TranslateAccelerator (0x343a158)->(0x32c8fc)
fixme:shdocvw:InPlaceActiveObject_TranslateAccelerator (0x343a158)->(0x32c8fc)
fixme:shdocvw:InPlaceActiveObject_TranslateAccelerator (0x343a158)->(0x32c8fc)
fixme:shdocvw:InPlaceActiveObject_TranslateAccelerator (0x343a158)->(0x32c8fc)
fixme:mshtml:DispatchEx_GetDispID Unsupported grfdex 8
fixme:mshtml:DispatchEx_GetDispID Unsupported grfdex 8
fixme:mshtml:DispatchEx_GetDispID Unsupported grfdex 8
fixme:mshtml:DispatchEx_GetDispID Unsupported grfdex 8
fixme:mshtml:DispatchEx_GetDispID Unsupported grfdex 8
fixme:mshtml:DispatchEx_GetDispID Unsupported grfdex 8
fixme:shdocvw:InPlaceActiveObject_TranslateAccelerator (0x343a158)->(0x32c8fc)
fixme:shdocvw:InPlaceActiveObject_TranslateAccelerator (0x343a158)->(0x32c8fc)
fixme:shdocvw:InPlaceActiveObject_TranslateAccelerator (0x343a158)->(0x32c8fc)
fixme:shdocvw:InPlaceActiveObject_TranslateAccelerator (0x343a158)->(0x32c8fc)
fixme:shdocvw:InPlaceActiveObject_TranslateAccelerator (0x343a158)->(0x32c8fc)
fixme:mshtml:DispatchEx_GetDispID Unsupported grfdex 8
fixme:mshtml:DispatchEx_GetDispID Unsupported grfdex 8
fixme:mshtml:DispatchEx_GetDispID Unsupported grfdex 8
fixme:mshtml:DispatchEx_GetDispID Unsupported grfdex 8
fixme:mshtml:DispatchEx_GetDispID Unsupported grfdex 8
fixme:mshtml:DispatchEx_GetDispID Unsupported grfdex 8
fixme:mshtml:DispatchEx_GetDispID Unsupported grfdex 8
fixme:mshtml:DispatchEx_GetDispID Unsupported grfdex 8
fixme:mshtml:DispatchEx_GetDispID Unsupported grfdex 8
fixme:mshtml:DispatchEx_GetDispID Unsupported grfdex 8
fixme:mshtml:DispatchEx_GetDispID Unsupported grfdex 8
fixme:mshtml:DispatchEx_GetDispID Unsupported grfdex 8
fixme:mshtml:DispatchEx_GetDispID Unsupported grfdex 8
fixme:mshtml:DispatchEx_GetDispID Unsupported grfdex 8
fixme:mshtml:DispatchEx_GetDispID Unsupported grfdex 8
fixme:mshtml:DispatchEx_GetDispID Unsupported grfdex 8
fixme:mshtml:DispatchEx_GetDispID Unsupported grfdex 8
fixme:mshtml:DispatchEx_GetDispID Unsupported grfdex 8
fixme:mshtml:DispatchEx_GetDispID Unsupported grfdex 8
fixme:mshtml:DispatchEx_GetDispID Unsupported grfdex 8
fixme:mshtml:DispatchEx_GetDispID Unsupported grfdex 8
fixme:mshtml:DispatchEx_GetDispID Unsupported grfdex 8
fixme:mshtml:DispatchEx_GetDispID Unsupported grfdex 8
fixme:mshtml:DispatchEx_GetDispID Unsupported grfdex 8
fixme:mshtml:DispatchEx_GetDispID Unsupported grfdex 8
fixme:mshtml:DispatchEx_GetDispID Unsupported grfdex 8
fixme:shdocvw:InPlaceActiveObject_TranslateAccelerator (0x343a158)->(0x32c8fc)
fixme:shdocvw:InPlaceActiveObject_TranslateAccelerator (0x343a158)->(0x32c8fc)
fixme:shdocvw:InPlaceActiveObject_TranslateAccelerator (0x343a158)->(0x32c8fc)
fixme:shdocvw:InPlaceActiveObject_TranslateAccelerator (0x343a158)->(0x32c8fc)
fixme:shdocvw:InPlaceActiveObject_TranslateAccelerator (0x343a158)->(0x32c8fc)
fixme:shdocvw:InPlaceActiveObject_TranslateAccelerator (0x343a158)->(0x32c8fc)
fixme:shdocvw:InPlaceActiveObject_TranslateAccelerator (0x343a158)->(0x32c8fc)
fixme:shdocvw:InPlaceActiveObject_TranslateAccelerator (0x343a158)->(0x32c8fc)
fixme:mshtml:DispatchEx_GetDispID Unsupported grfdex 8
fixme:mshtml:DispatchEx_GetDispID Unsupported grfdex 8
fixme:mshtml:DispatchEx_GetDispID Unsupported grfdex 8
fixme:mshtml:DispatchEx_GetDispID Unsupported grfdex 8
fixme:mshtml:DispatchEx_GetDispID Unsupported grfdex 8
fixme:mshtml:DispatchEx_GetDispID Unsupported grfdex 8
fixme:shdocvw:InPlaceActiveObject_TranslateAccelerator (0x343a158)->(0x32c8fc)
fixme:shdocvw:InPlaceActiveObject_TranslateAccelerator (0x343a158)->(0x32bfa0)
fixme:shdocvw:InPlaceActiveObject_TranslateAccelerator (0x343a158)->(0x32c8fc)
fixme:shdocvw:InPlaceActiveObject_TranslateAccelerator (0x343a158)->(0x32c8fc)
fixme:shdocvw:InPlaceActiveObject_TranslateAccelerator (0x343a158)->(0x32c8fc)
fixme:shdocvw:InPlaceActiveObject_TranslateAccelerator (0x343a158)->(0x32c8fc)
fixme:shdocvw:InPlaceActiveObject_TranslateAccelerator (0x343a158)->(0x32c8fc)
fixme:shdocvw:InPlaceActiveObject_TranslateAccelerator (0x343a158)->(0x32c8fc)
fixme:shdocvw:InPlaceActiveObject_TranslateAccelerator (0x343a158)->(0x32c8fc)
fixme:shdocvw:InPlaceActiveObject_TranslateAccelerator (0x343a158)->(0x32c8fc)
fixme:shdocvw:InPlaceActiveObject_TranslateAccelerator (0x343a158)->(0x32c8fc)
fixme:mshtml:DispatchEx_GetDispID Unsupported grfdex 8
fixme:mshtml:DispatchEx_GetDispID Unsupported grfdex 8
fixme:mshtml:DispatchEx_GetDispID Unsupported grfdex 8
fixme:mshtml:DispatchEx_GetDispID Unsupported grfdex 8
fixme:mshtml:DispatchEx_GetDispID Unsupported grfdex 8
fixme:mshtml:DispatchEx_GetDispID Unsupported grfdex 8
fixme:shdocvw:InPlaceActiveObject_TranslateAccelerator (0x343a158)->(0x32c8fc)
fixme:shdocvw:InPlaceActiveObject_TranslateAccelerator (0x343a158)->(0x32c8fc)
fixme:shdocvw:InPlaceActiveObject_TranslateAccelerator (0x343a158)->(0x32c8fc)
fixme:shdocvw:InPlaceActiveObject_TranslateAccelerator (0x343a158)->(0x32c8fc)
fixme:shdocvw:InPlaceActiveObject_TranslateAccelerator (0x343a158)->(0x32c8fc)
fixme:shdocvw:InPlaceActiveObject_TranslateAccelerator (0x343a158)->(0x32c8fc)
fixme:shdocvw:InPlaceActiveObject_TranslateAccelerator (0x343a158)->(0x32bfa0)
fixme:shdocvw:InPlaceActiveObject_TranslateAccelerator (0x343a158)->(0x32c8fc)
fixme:shdocvw:InPlaceActiveObject_TranslateAccelerator (0x343a158)->(0x32c8fc)
fixme:shdocvw:InPlaceActiveObject_TranslateAccelerator (0x343a158)->(0x32c8fc)
fixme:shdocvw:InPlaceActiveObject_TranslateAccelerator (0x343a158)->(0x32c8fc)
fixme:shdocvw:InPlaceActiveObject_TranslateAccelerator (0x343a158)->(0x32c8fc)
fixme:mshtml:DispatchEx_GetDispID Unsupported grfdex 8
fixme:mshtml:DispatchEx_GetDispID Unsupported grfdex 8
fixme:mshtml:DispatchEx_GetDispID Unsupported grfdex 8
fixme:mshtml:DispatchEx_GetDispID Unsupported grfdex 8
fixme:mshtml:DispatchEx_GetDispID Unsupported grfdex 8
fixme:mshtml:DispatchEx_GetDispID Unsupported grfdex 8
fixme:shdocvw:InPlaceActiveObject_TranslateAccelerator (0x343a158)->(0x32c8fc)
fixme:shdocvw:InPlaceActiveObject_TranslateAccelerator (0x343a158)->(0x32c8fc)
fixme:shdocvw:InPlaceActiveObject_TranslateAccelerator (0x343a158)->(0x32c8fc)
fixme:shdocvw:InPlaceActiveObject_TranslateAccelerator (0x343a158)->(0x32c8fc)
fixme:mshtml:DispatchEx_GetDispID Unsupported grfdex 8
fixme:mshtml:DispatchEx_GetDispID Unsupported grfdex 8
fixme:mshtml:DispatchEx_GetDispID Unsupported grfdex 8
fixme:mshtml:DispatchEx_GetDispID Unsupported grfdex 8
fixme:mshtml:DispatchEx_GetDispID Unsupported grfdex 8
fixme:mshtml:DispatchEx_GetDispID Unsupported grfdex 8
fixme:mshtml:DispatchEx_GetDispID Unsupported grfdex 8
fixme:mshtml:DispatchEx_GetDispID Unsupported grfdex 8
fixme:mshtml:DispatchEx_GetDispID Unsupported grfdex 8
fixme:mshtml:DispatchEx_GetDispID Unsupported grfdex 8
fixme:mshtml:DispatchEx_GetDispID Unsupported grfdex 8
fixme:mshtml:DispatchEx_GetDispID Unsupported grfdex 8
fixme:mshtml:DispatchEx_GetDispID Unsupported grfdex 8
fixme:mshtml:DispatchEx_GetDispID Unsupported grfdex 8
fixme:mshtml:DispatchEx_GetDispID Unsupported grfdex 8
fixme:mshtml:DispatchEx_GetDispID Unsupported grfdex 8
fixme:mshtml:DispatchEx_GetDispID Unsupported grfdex 8
fixme:mshtml:DispatchEx_GetDispID Unsupported grfdex 8
fixme:mshtml:DispatchEx_GetDispID Unsupported grfdex 8
fixme:mshtml:DispatchEx_GetDispID Unsupported grfdex 8
fixme:mshtml:DispatchEx_GetDispID Unsupported grfdex 8
fixme:mshtml:DispatchEx_GetDispID Unsupported grfdex 8
fixme:mshtml:DispatchEx_GetDispID Unsupported grfdex 8
fixme:mshtml:DispatchEx_GetDispID Unsupported grfdex 8
fixme:mshtml:DispatchEx_GetDispID Unsupported grfdex 8
fixme:mshtml:DispatchEx_GetDispID Unsupported grfdex 8
fixme:mshtml:DispatchEx_GetDispID Unsupported grfdex 8
fixme:mshtml:DispatchEx_GetDispID Unsupported grfdex 8
fixme:mshtml:DispatchEx_GetDispID Unsupported grfdex 8
fixme:mshtml:DispatchEx_GetDispID Unsupported grfdex 8
fixme:mshtml:DispatchEx_GetDispID Unsupported grfdex 8
fixme:mshtml:DispatchEx_GetDispID Unsupported grfdex 8
fixme:mshtml:DispatchEx_GetDispID Unsupported grfdex 8
fixme:mshtml:DispatchEx_GetDispID Unsupported grfdex 8
fixme:mshtml:DispatchEx_GetDispID Unsupported grfdex 8
fixme:mshtml:DispatchEx_GetDispID Unsupported grfdex 8
fixme:mshtml:DispatchEx_GetDispID Unsupported grfdex 8
fixme:mshtml:DispatchEx_GetDispID Unsupported grfdex 8
fixme:mshtml:DispatchEx_GetDispID Unsupported grfdex 8
fixme:mshtml:DispatchEx_GetDispID Unsupported grfdex 8
fixme:mshtml:DispatchEx_GetDispID Unsupported grfdex 8
fixme:mshtml:DispatchEx_GetDispID Unsupported grfdex 8
fixme:mshtml:DispatchEx_GetDispID Unsupported grfdex 8
fixme:mshtml:DispatchEx_GetDispID Unsupported grfdex 8
fixme:mshtml:DispatchEx_GetDispID Unsupported grfdex 8
fixme:mshtml:DispatchEx_GetDispID Unsupported grfdex 8
fixme:mshtml:DispatchEx_GetDispID Unsupported grfdex 8
fixme:mshtml:DispatchEx_GetDispID Unsupported grfdex 8
fixme:mshtml:DispatchEx_GetDispID Unsupported grfdex 8
fixme:mshtml:DispatchEx_GetDispID Unsupported grfdex 8
fixme:mshtml:DispatchEx_GetDispID Unsupported grfdex 8
fixme:mshtml:DispatchEx_GetDispID Unsupported grfdex 8
fixme:mshtml:DispatchEx_GetDispID Unsupported grfdex 8
fixme:mshtml:DispatchEx_GetDispID Unsupported grfdex 8
fixme:mshtml:DispatchEx_GetDispID Unsupported grfdex 8
fixme:mshtml:DispatchEx_GetDispID Unsupported grfdex 8
fixme:mshtml:DispatchEx_GetDispID Unsupported grfdex 8
fixme:mshtml:DispatchEx_GetDispID Unsupported grfdex 8
fixme:mshtml:DispatchEx_GetDispID Unsupported grfdex 8
fixme:mshtml:DispatchEx_GetDispID Unsupported grfdex 8
fixme:mshtml:DispatchEx_GetDispID Unsupported grfdex 8
fixme:mshtml:DispatchEx_GetDispID Unsupported grfdex 8
fixme:mshtml:DispatchEx_GetDispID Unsupported grfdex 8
fixme:mshtml:DispatchEx_GetDispID Unsupported grfdex 8
fixme:mshtml:DispatchEx_GetDispID Unsupported grfdex 8
fixme:mshtml:DispatchEx_GetDispID Unsupported grfdex 8
fixme:mshtml:DispatchEx_GetDispID Unsupported grfdex 8
fixme:mshtml:DispatchEx_GetDispID Unsupported grfdex 8
fixme:mshtml:DispatchEx_GetDispID Unsupported grfdex 8
fixme:mshtml:DispatchEx_GetDispID Unsupported grfdex 8
fixme:mshtml:DispatchEx_GetDispID Unsupported grfdex 8
fixme:mshtml:DispatchEx_GetDispID Unsupported grfdex 8
fixme:mshtml:DispatchEx_GetDispID Unsupported grfdex 8
fixme:mshtml:DispatchEx_GetDispID Unsupported grfdex 8
fixme:mshtml:DispatchEx_GetDispID Unsupported grfdex 8
fixme:mshtml:DispatchEx_GetDispID Unsupported grfdex 8
fixme:mshtml:DispatchEx_GetDispID Unsupported grfdex 8
fixme:mshtml:DispatchEx_GetDispID Unsupported grfdex 8
fixme:mshtml:DispatchEx_GetDispID Unsupported grfdex 8
fixme:mshtml:DispatchEx_GetDispID Unsupported grfdex 8
fixme:mshtml:DispatchEx_GetDispID Unsupported grfdex 8
fixme:mshtml:DispatchEx_GetDispID Unsupported grfdex 8
fixme:mshtml:DispatchEx_GetDispID Unsupported grfdex 8
fixme:mshtml:DispatchEx_GetDispID Unsupported grfdex 8
fixme:mshtml:DispatchEx_GetDispID Unsupported grfdex 8
fixme:mshtml:DispatchEx_GetDispID Unsupported grfdex 8
fixme:mshtml:DispatchEx_GetDispID Unsupported grfdex 8
fixme:mshtml:DispatchEx_GetDispID Unsupported grfdex 8
fixme:mshtml:DispatchEx_GetDispID Unsupported grfdex 8
fixme:mshtml:DispatchEx_GetDispID Unsupported grfdex 8
fixme:mshtml:DispatchEx_GetDispID Unsupported grfdex 8
fixme:mshtml:DispatchEx_GetDispID Unsupported grfdex 8
fixme:mshtml:DispatchEx_GetDispID Unsupported grfdex 8
fixme:mshtml:DispatchEx_GetDispID Unsupported grfdex 8
fixme:mshtml:DispatchEx_GetDispID Unsupported grfdex 8
fixme:mshtml:DispatchEx_GetDispID Unsupported grfdex 8
fixme:mshtml:DispatchEx_GetDispID Unsupported grfdex 8
fixme:mshtml:DispatchEx_GetDispID Unsupported grfdex 8
fixme:mshtml:DispatchEx_GetDispID Unsupported grfdex 8
fixme:mshtml:DispatchEx_GetDispID Unsupported grfdex 8
fixme:shdocvw:InPlaceActiveObject_TranslateAccelerator (0x343a158)->(0x32de88)
fixme:shdocvw:InPlaceActiveObject_TranslateAccelerator (0x343a158)->(0x32cec4)
fixme:mshtml:DispatchEx_GetDispID Unsupported grfdex 8
fixme:mshtml:DispatchEx_GetDispID Unsupported grfdex 8
fixme:mshtml:DispatchEx_GetDispID Unsupported grfdex 8
fixme:mshtml:DispatchEx_GetDispID Unsupported grfdex 8
fixme:mshtml:DispatchEx_GetDispID Unsupported grfdex 8
fixme:mshtml:DispatchEx_GetDispID Unsupported grfdex 8
fixme:shdocvw:InPlaceActiveObject_TranslateAccelerator (0x343a158)->(0x32d040)
fixme:shdocvw:InPlaceActiveObject_TranslateAccelerator (0x343a158)->(0x32c07c)
fixme:mshtml:DispatchEx_GetDispID Unsupported grfdex 8
fixme:mshtml:DispatchEx_GetDispID Unsupported grfdex 8
fixme:mshtml:DispatchEx_GetDispID Unsupported grfdex 8
fixme:mshtml:DispatchEx_GetDispID Unsupported grfdex 8
fixme:mshtml:DispatchEx_GetDispID Unsupported grfdex 8
fixme:mshtml:DispatchEx_GetDispID Unsupported grfdex 8
fixme:mshtml:DispatchEx_GetDispID Unsupported grfdex 8
fixme:mshtml:DispatchEx_GetDispID Unsupported grfdex 8
fixme:mshtml:DispatchEx_GetDispID Unsupported grfdex 8
fixme:mshtml:DispatchEx_GetDispID Unsupported grfdex 8
fixme:mshtml:DispatchEx_GetDispID Unsupported grfdex 8
fixme:mshtml:DispatchEx_GetDispID Unsupported grfdex 8
fixme:mshtml:DispatchEx_GetDispID Unsupported grfdex 8
fixme:mshtml:DispatchEx_GetDispID Unsupported grfdex 8
fixme:mshtml:DispatchEx_GetDispID Unsupported grfdex 8
fixme:mshtml:DispatchEx_GetDispID Unsupported grfdex 8
fixme:mshtml:DispatchEx_GetDispID Unsupported grfdex 8
fixme:mshtml:DispatchEx_GetDispID Unsupported grfdex 8
fixme:mshtml:DispatchEx_GetDispID Unsupported grfdex 8
fixme:mshtml:DispatchEx_GetDispID Unsupported grfdex 8
fixme:mshtml:DispatchEx_GetDispID Unsupported grfdex 8
fixme:mshtml:DispatchEx_GetDispID Unsupported grfdex 8
fixme:mshtml:DispatchEx_GetDispID Unsupported grfdex 8
fixme:mshtml:DispatchEx_GetDispID Unsupported grfdex 8
fixme:mshtml:DispatchEx_GetDispID Unsupported grfdex 8
fixme:mshtml:DispatchEx_GetDispID Unsupported grfdex 8
fixme:mshtml:DispatchEx_GetDispID Unsupported grfdex 8
fixme:mshtml:DispatchEx_GetDispID Unsupported grfdex 8
fixme:mshtml:DispatchEx_GetDispID Unsupported grfdex 8
fixme:mshtml:DispatchEx_GetDispID Unsupported grfdex 8
fixme:mshtml:DispatchEx_GetDispID Unsupported grfdex 8
fixme:mshtml:DispatchEx_GetDispID Unsupported grfdex 8
fixme:mshtml:DispatchEx_GetDispID Unsupported grfdex 8
fixme:mshtml:DispatchEx_GetDispID Unsupported grfdex 8
fixme:mshtml:DispatchEx_GetDispID Unsupported grfdex 8
fixme:mshtml:DispatchEx_GetDispID Unsupported grfdex 8
fixme:mshtml:DispatchEx_GetDispID Unsupported grfdex 8
fixme:mshtml:DispatchEx_GetDispID Unsupported grfdex 8
fixme:mshtml:DispatchEx_GetDispID Unsupported grfdex 8
fixme:mshtml:DispatchEx_GetDispID Unsupported grfdex 8
fixme:mshtml:DispatchEx_GetDispID Unsupported grfdex 8
fixme:mshtml:DispatchEx_GetDispID Unsupported grfdex 8
err:ole:CoGetClassObject class {9a5ea990-3034-4d6f-9128-01f3c61022bc} not registered
err:ole:CoGetClassObject no class object {9a5ea990-3034-4d6f-9128-01f3c61022bc} could be created for context 0x1
fixme:win:EnumDisplayDevicesW ((null),0,0x32cee4,0x00000000), stub!
fixme:shdocvw:ViewObject_SetAdvise (0xf53a140)->(1 00000002 0x26a6870)
fixme:shdocvw:PersistStreamInit_InitNew (0xf53a140)
fixme:shdocvw:WebBrowser_put_RegisterAsBrowser (0xf53a140)->(ffffffff)
fixme:shdocvw:WebBrowser_put_RegisterAsDropTarget (0xf53a140)->(ffffffff)
fixme:shdocvw:OleInPlaceObject_InPlaceDeactivate (0xf53a140)
fixme:shdocvw:OleInPlaceObject_UIDeactivate (0xf53a140)
fixme:shdocvw:OleObject_Close (0xf53a140)->(1)
fixme:win:EnumDisplayDevicesW ((null),0,0x33f264,0x00000000), stub!
fixme:mshtml:hidden_proc (0x100ba 49236 0 1)
fixme:win:EnumDisplayDevicesW ((null),0,0x33f26c,0x00000000), stub!
fixme:mshtml:hidden_proc (0x100ba 49236 0 1)
CellID: Connecting to 117.121.248.122:27031. . .
CellID: Connect to 117.121.248.122:27031 took 324 MS
CellID: Nothing beat our old best time of 25 MS
CellID: Connecting to 79.141.165.4:27031. . .
CellID: Connect to 79.141.165.4:27031 took 159 MS
CellID: Nothing beat our old best time of 25 MS
CellID: Connecting to 63.150.161.165:27031. . .
CellID: Connect to 63.150.161.165:27031 took 52 MS
CellID: Nothing beat our old best time of 25 MS
err:ole:CoGetClassObject class {77f10cf0-3db5-4966-b520-b7c54fd35ed6} not registered
err:ole:CoGetClassObject no class object {77f10cf0-3db5-4966-b520-b7c54fd35ed6} could be created for context 0x1
err:ole:RevokeDragDrop invalid hwnd 0x10040
err:ole:RevokeDragDrop invalid hwnd 0x10046
err:ole:RevokeDragDrop invalid hwnd 0x10048
err:ole:RevokeDragDrop invalid hwnd 0x1004a
err:ole:RevokeDragDrop invalid hwnd 0x1005e
fixme:win:UnregisterDeviceNotification (handle=0xcafecafe), STUB!
err:ole:RevokeDragDrop invalid hwnd 0x10094
err:ole:RevokeDragDrop invalid hwnd 0x10096
err:ole:RevokeDragDrop invalid hwnd 0x10098
err:ole:RevokeDragDrop invalid hwnd 0x1009a
err:ole:RevokeDragDrop invalid hwnd 0x1009c
err:ole:RevokeDragDrop invalid hwnd 0x1009e
err:ole:RevokeDragDrop invalid hwnd 0x100a0
err:ole:RevokeDragDrop invalid hwnd 0x100a2
err:ole:RevokeDragDrop invalid hwnd 0x1004c
err:ole:RevokeDragDrop invalid hwnd 0x1004e
err:ole:RevokeDragDrop invalid hwnd 0x2003c
fixme:shdocvw:OleInPlaceObject_InPlaceDeactivate (0x34384a8)
fixme:shdocvw:OleInPlaceObject_UIDeactivate (0x34384a8)
fixme:shdocvw:OleObject_Close (0x34384a8)->(1)
fixme:shdocvw:OleInPlaceObject_InPlaceDeactivate (0x343a158)
fixme:shdocvw:OleInPlaceObject_UIDeactivate (0x343a158)
fixme:shdocvw:OleObject_Close (0x343a158)->(1)
fixme:mshtml:HlinkTarget_SetBrowseContext (0x3447778)->((nil))
Shutting down. . .
fixme:winmm:MMDRV_Exit Closing while ll-driver open
fixme:winmm:MMDRV_Exit Closing while ll-driver open

```

---

