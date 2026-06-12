---
title: "how do i change the graphic driver settings for wine?"
date: 2010-07-14
forum: Wine
---

### Post by opendevlite on 2010-07-14
i just installed and can login to a Ragnarok Online game, using wine

my problem is that, the graphics are very slow, even from starting, the game and from the login screen,

i tried changing the graphic driver of Ragnarok from its Setup.exe, which has three settings "Wine D3D7 T&L HAL", "Wine D3D7 HAL", "Wine D3D7 RGB", but still very slow

i need help

---

### Post by cogadh on 2010-07-14
Wine just uses whatever driver you have already installed in Linux, you can't really change that (other than updating the Linux graphics driver). What kind of video hardware do you have?

---

### Post by opendevlite on 2010-07-14
its a "Inno3d Geforce FX5200" graphics card

i didn't have any problems, with this card on "Windows XP"

---

### Post by cogadh on 2010-07-14
Ubuntu is not Windows XP, you can't compare the two, especially when trying to run a Windows game on Ubuntu with Wine. Because you are trying to run the game through a compatibility layer, you should expect at least a minor performance hit, perhaps worse. Have you checked the AppDB entry for the game to see if it offers any configuration tweaks?
[http://appdb.winehq.org/](http://appdb.winehq.org/)

---

### Post by opendevlite on 2010-07-14
i already did

most of the comments are, very old, even though, i really didn't find anything useful

---

### Post by hikaricore on 2010-07-14
If you're not going to reply with useful information don't expect anyone to help you further.
More than likely your card is no longer supported by the ati proprietary driver or you didn't properly enable it.

---

### Post by cogadh on 2010-07-14
Considering he has an Nvidia card, I seriously doubt that is the issue. Speaking from personal experience with that particular card, it does not have the greatest performance to start with. It is a budget model from 7 years ago and even though RO isn't that demanding a game, combined with Wine, it might not be enough to get smooth gameplay.

---

### Post by asdfoo on 2010-07-14
since you haven't mentioned which version of Wine you're using, I'd suggest trying out the most recent version which is 1.2-rc7.

open a terminal and type 'wine --version' to find out which one you have.

I have this card in an older machine and it works ok for some games but it's not spectacular.  As others have suggested, a newer card may provide better results.

---

### Post by hikaricore on 2010-07-14
I misread his card name as an ati model, my other points still stand.
He needs to be more cooperative with his replies and check his damn drviers.

---

