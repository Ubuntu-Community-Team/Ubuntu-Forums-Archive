---
title: "Black screen of death?"
date: 2009-05-26
forum: Wine
---

### Post by God of the Meeps on 2009-05-26
[FONT="Verdana"][COLOR="Magenta"]I just loaded Ubuntu on my computer, and loaded up GuildWars with WINE.

The initial installation and everything seemed to go fine, but when I booted up GuildWars, all I got was a black and blue screen.

Any suggestions for why this might happen? [/COLOR][/FONT]

---

### Post by asdfoo on 2009-05-26
> **God of the Meeps said:**
> I just loaded Ubuntu on my computer, and loaded up GuildWars with Wine.

The initial installation and everything seemed to go fine, but when I booted up GuildWars, all I got was a black and blue screen.

Any suggestions for why this might happen? 

Your forum posting colour is criminal... please don't do that.

Which Wine version?
Which video card and drivers?

---

### Post by hikaricore on 2009-05-27
> **asdfoo said:**
> Your forum posting colour is criminal... please don't do that.

I quite enjoy it.  Speak for yourself.  :p

---

### Post by Duskao on 2009-05-27
I have no problems with the text colour myself. :D. How much have you tried tweaking guild wars with wine? First off, I would recommend, at least till you get it going better, emulate a desktop through configure wine. Also within configure wine, try it with and without pixel shader under the graphics tab. 

A couple other things you can try are the regedit Direct3D tweaks. fbo and set your ram. Look here [http://wiki.winehq.org/UsefulRegistryKeys](http://wiki.winehq.org/UsefulRegistryKeys) 

If none of that works you gotta go to the source! Look here [http://appdb.winehq.org/objectManager.php?sClass=version&iId=9194](http://appdb.winehq.org/objectManager.php?sClass=version&iId=9194)

Be sure you are using the newest driver for your video card. Best of luck.

---

### Post by God of the Meeps on 2009-05-27
[FONT="Verdana"]My graphics card is the Intel GMA x3100, and I will be testing out the other options soon (I'm looking for the drivers)

Thanks for the help so far, guys.[/FONT]

---

### Post by God of the Meeps on 2009-05-27
It turns out that it probably wasn't the video card, but the pixel shader. The login screen now works. Thanks guys, for the help.

---

### Post by God of the Meeps on 2009-05-27
[FONT="Verdana"]Nevermind, even though the login screen seems to work, the 3D renderer has died. The characters create trails, and occasionally fade to white. Suggestions?[/FONT]

---

### Post by alex.rayu on 2009-05-27
At least it's black, the suitable color.

---

