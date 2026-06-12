---
title: "Star Wars KOTOR w/WINE troubles"
date: 2010-03-03
forum: Wine
---

### Post by jmviles on 2010-03-03
I have been trying to get Star Wars: Knights of the Old Republic to work in wine.  I have been using the PlayOnLinux frontend and am using Karmic.  I was able to install the game without too much trouble with the playonlinux installer, but I did have to use the no-cd crack to get it to load the menu.  

My problem is that when I try to run the game (through the playonlinux menu) I will see the credit screens and then a black screen or I will just hear the sounds of the credit screen and then get a messed up menu screen with a crude 3d man standing cross armed and a menu that is unresponsive to mouse or keyboard.  Sometimes I don't get to see the credits and the menu shows up black.

I am not very well versed in how to use wine as this is my first attempt so please be patient with me.  

Thanks.

---

### Post by jmviles on 2010-03-03
Well, I got the game to load finally by using wine cfg and checking the emulate desktop option.  My problem now is that the graphics are very poor.  The menus are mostly white and the characters are all lacking anything beyond their basic shape.  
I am using a Thinkpad r500
Intel Core 2 Duo 2.26 GHZ
1 MB RAM
GNOME 2.28.1
I just updated WINE so I think whatever version I have is the newest.
Intel Graphics Media Accelerator (GMA) 4500MHD

Oh and since I started using the desktop emulation I have been getting this error message:
mmap() failed: Cannot allocate memory
repeated 8 times.

I have a sneaking suspicion that the crappy built in graphics card on these machines won't support the game, but if anyone knows another reason it would be messing up like this I would sure appreciate the help.

---

### Post by Ferrat on 2010-03-03
It's most likely your graphic card that is the reason, Intel drivers for Linux are really bad :/

---

### Post by BbUiDgZ on 2010-03-03
> **Ferrat said:**
> It's most likely your graphic card that is the reason

thats what i was thinking when i read this

---

### Post by IceDoE on 2010-03-03
I'm a bit surprised you got it working at all. You aren't using the Best of PC version are you? I have that and its given me all kinds of trouble trying to get it to install and run under WINE. Of course, the game in the pack I'm most interested in is Battlefront, but I think if you could get that running at all, it should be possible for Battlefront.

---

### Post by 1492 on 2010-11-18
I use KOTOR from the Best of PC pack and it runs perfectly (absolutely no problems at all) . If the graphics problem you are having are the same as mine, just press esc and the a menu that is not distorted or anything should come up. Just mess with the graphics until it is normal. If you are using Best of PC I'm not sure how you managed to get Play On Linux to install it because I could not get any of them to work with it. I just found went to setup.exe on the cd & opened it with winecore. Then to run it, the launcher won't work, so you have to browse C: drive & find launcher.exe. Also, about Intel, that's what's on my computer & hasn't caused any problems in Linux. I use it with Wine 1.2

---

