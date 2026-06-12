---
title: "How to install Sins of Solar Empire?"
date: 2009-07-07
forum: Wine
---

### Post by Melhisedek on 2009-07-07
I bought the game through Impulse so I don't have any physical media. How do I get it to work? (have it on my Windows partition)

---

### Post by cogadh on 2009-07-08
All you should need to do is copy the install executable you downloaded through Impulse to your Linux partition, then run the install just like you did on Windows, assuming that you already have Wine installed and configured.

---

### Post by Melhisedek on 2009-07-08
Worked wonderfully but sadly font is to big, and I can't increase resolution to my native. Any ideas on how I could fix that perhaps? I think there was a thing I could do about fonts but not sure about resolution...

Solved both problems :) Fonts can be get from here:

[www.honorguardonline.com/sins/sinsfontfix.tar.gz](www.honorguardonline.com/sins/sinsfontfix.tar.gz)

and resolution was fixed by:
```

Make sure it's not running in windowed mode. if that fails, try changing it manually via the setting config files:

C:\Documents and Settings\<account_name>\Local Settings\Application Data\Ironclad Games\Sins of a Solar Empire\Setting

"user.setting" - open with notepad or any text editor.

VideoFullScreenWidth ####
VideoFullScreenHeight #### - change to what you want them to be and save.

```

---

### Post by BlackRoijaX on 2009-07-08
Buying any game that doesn't have a physical media is a very, very, very bad idea.

---

### Post by Melhisedek on 2009-07-08
I just wanted to support the publisher for not including any DRM whatsoever. Have all the Stardock games. Never even played Galactic Civilizations for more than 2 hours (couldn't get what I was supposed to do) Demigod I did 2 MP matches, still I want to support them

---

### Post by cogadh on 2009-07-08
> **BlackRoijaX said:**
> Buying any game that doesn't have a physical media is a very, very, very bad idea.

Its only a bad idea if you don't have the means to back up the downloaded data. Pretty much everyone should have some kind of CD/DVD burner these days, so that really shouldn't be an issue. Buying digitally distributed games is not only easier, it is (often) cheaper and much more environmentally friendly. Pretty much its a good thing all around, especially when you are supporting a company that is on the gamer's side, like Stardock.

---

### Post by BlackRoijaX on 2009-07-08
> **cogadh said:**
> Its only a bad idea if you don't have the means to back up the downloaded data. Pretty much everyone should have some kind of CD/DVD burner these days, so that really shouldn't be an issue. Buying digitally distributed games is not only easier, it is (often) cheaper and much more environmentally friendly. Pretty much its a good thing all around, especially when you are supporting a company that is on the gamer's side, like Stardock.

Friendly smendly. If it doesn't have a real world presence, screw it.

---

### Post by not a pipe on 2009-07-11
> **BlackRoijaX said:**
> Buying any game that doesn't have a physical media is a very, very, very bad idea.

Heh, buying a game that requires ie7 to get updates is also a bad idea.

---

### Post by Sealbhach on 2010-05-30
SSE is being sold at a big discount now, it £2.76 in my currency:

[http://www.impulsedriven.com/sin](http://www.impulsedriven.com/sin)

I downloaded and install it using the Steam-like Impulse Client using Windows in Virtualbox. Then copied the installed folder into Linux and ran it in Wine. Works fine and good value at that price.

.

---

