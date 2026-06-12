---
title: "How-to What is up with Eve-online? [solution]"
date: 2009-02-15
forum: Wine
---

### Post by Selcal on 2009-02-15
**For NVIDIA drivers**
So i have found that with an nvidia graphics card that the debian distro of eve online works just fine when you download from here
[[COLOR="DarkOrange"]http://ccp.vo.llnwd.net/o2/linux/eve_000066_all.deb[/COLOR]]("http://ccp.vo.llnwd.net/o2/linux/eve_000066_all.deb")

But unfortunately my laptop has an ATI card and I was required to use the restricted drivers and fglrx.  So what is my options?

**For ATI drivers**
I found the solution for ATI to be in WINE
> sudo apt-get install wine
 and installing the stripped down windows version of the game from here.
[[COLOR="DarkOrange"]http://ccp.vo.llnwd.net/o2/EVE_Classic_Setup_75883.exe[/COLOR]]("http://ccp.vo.llnwd.net/o2/EVE_Classic_Setup_75883.exe")

Now I came accross an issue with text.  I could not read the EULA and even in the settings menu most of the information was unreadable.  I found in the eve online forums that it is required to install window$ fonts before continuing.  I found msttcorefonts and installed it.
> sudo apt-get install msttcorefonts
but even with this package installed I was unable to see the text and continue the game.  I found in the eve wiki that you need to copy the font to the proper location.  You can do this by typing:
> sudo cp /usr/share/fonts/truetype/msttcorefonts/* ~/.wine/drive_c/windows/Fonts

This worked well for me on my ATI graphics card laptop.  If this helps anyone else out please respond, I am only trying to get more EVE players linux ready for when the revolution comes ;)

BTW my name in EVE is "Facetiousproxy" look me up

---

### Post by dmizer on 2009-02-16
Moved this to the Gaming and Leisure section of the forums because it relies on offsite resources.

Thanks :)

---

### Post by v1nsai on 2009-12-17
a bit old but thanks for the quick tips, I knew the ms ttf fonts had to be in the repos, apt-cache failed me on this one I downloaded two packages that weren't that one.  Maybe they'll still work I don't know, still waiting on the game to download I'm thinking about turning my account back on.  Let me know if your still playing I don't know if any of my friends are still in New Eden.

---

