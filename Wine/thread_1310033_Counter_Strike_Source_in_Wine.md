---
title: "Counter Strike Source in Wine"
date: 2009-11-01
forum: Wine
---

### Post by baudday on 2009-11-01
I'm trying to play Counter Strike Source in Wine, and it runs fine. I have it set so it uses direct x 7.0 and that seems to make it run fast and all but the sound is delayed by about a half second using ALSA and OSS doesn't work at all. Also, it seems to crash 20 minutes into playtime every time without fail. No huge explosions or anything, just at the same point every time, it will crash. Anyone know how to fix this?

---

### Post by Sindwiller on 2009-11-01
[CS:S WineHQ AppDB page]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=3731&iTestingId=44488"), which will lead you to (pretty much in the middle of the page, below "Known issues":

> Game crashes after a few minutes. You can fix this by putting [this file]("http://bugs.winehq.org/attachment.cgi?id=18679") into your "~/.wine/drive_c/Program Files/Steam/steamapps/YOURUSERNAME/counter-strike source/cstrike/resource" folder, or by applying [this patch]("http://bugs.winehq.org/attachment.cgi?id=6853"). See bug [#7698]("http://bugs.winehq.org/show_bug.cgi?id=7698") for more information. 

---

### Post by baudday on 2009-11-01
I will try that as soon as I get a chance. Thank you so much for the prompt response!

---

### Post by baudday on 2009-11-01
Man I wish that worked, but at exactly the same time again. Anyone else know what could be causing this?

---

### Post by beastrace91 on 2009-11-02
Wine version, video card, and driver version?

~Jeff

---

### Post by baudday on 2009-11-02
Could you point me to where I can find some of that info? I have an ATI Radeon Platinum X850 card, and I use EnvyNG for drivers, so I have the 8.543-0ubuntu4.1 driver installed which uses fglrx. I'm able to run world of warcraft great with this set up and I know the card is powerful enough to run the game cause I had no problems with it when I ran the game in Windows when I had Windows. If you could show me how to get the Wine version, I'm not sure where to find that. But it's one update off from the very latest version.

---

### Post by baudday on 2009-11-02
oh wait okay I found it. I have version 1.1.31

---

### Post by baudday on 2009-11-02
bump

---

### Post by beastrace91 on 2009-11-02
No need to bump I will check back...

Try a different Wine version (latest is 1.1.32 or the older .28 or .29 work well for CSS I know). Also just as a heads up ATI drivers for Linux are a joke at best. Random stability issues you may experience running 3D applications (especially Wined programs) may very well be the fault of the ATI card.

~Jeff

---

### Post by baudday on 2009-11-02
I will try it with Wine upgraded, but how do I go back down to say version .28?

Edit: Never mind, I found it.

---

### Post by baudday on 2009-11-02
well, i tried running it in .28 and it seemed like it was running faster, but it still crashed, and it actually crashed a little earlier than normal. i guess i just don't understand how my card/drivers can handle world of warcraft with the settings turned up fairly high, but can't handle counter strike.

---

### Post by baudday on 2009-11-02
I just discovered when a download takes too long such as a map or some sounds, it will freeze up in the middle of the download. I can still move the mouse, but clicking anything does nothing, and the keyboard completely locks up. I don't think it's my graphics card, because nothing graphically intensive is happening when it's downloading to cause this. I may just have it set up wrong in wine?

---

### Post by Koosti on 2009-11-02
> **baudday said:**
> I just discovered when a download takes too long such as a map or some sounds, it will freeze up in the middle of the download. I can still move the mouse, but clicking anything does nothing, and the keyboard completely locks up. I don't think it's my graphics card, because nothing graphically intensive is happening when it's downloading to cause this. I may just have it set up wrong in wine?

It appears I'm getting pretty much the same results.

Either I do get ingame and it will crash without fail, or then my whole system seems to lock up and I need to use the power switch to restart my computer. The latter usually comes up during connecting to a server or downloading custom content (maps, sounds, etc)

Possibly something to do with ATI cards / drivers, since I'm using one as well?

---

### Post by beastrace91 on 2009-11-02
> **Koosti said:**
> Possibly something to do with ATI cards / drivers, since I'm using one as well?

Yep. I'd be willing to bet a large sum of cash that is the culprit. The fact is if you want to attempt gaming on Linux at all (namely Windows games under some form of Wine software) nVidia is the only way to go to get the best/stable results across the board.

That being said odds are if you want to keep a stable game play for CSS go grab an nVidia chip or dual boot :/

~Jeff

---

### Post by baudday on 2009-11-02
Man that is a bummer. I was really hoping against all odds I could get this working. That's how it felt with wow, but I was able to get it running completely stable. Guess Ubuntu just isn't good for ATI. Oh well...

---

### Post by beastrace91 on 2009-11-03
> **baudday said:**
> Guess Ubuntu just isn't good for ATI. 

ATI isn't good for Linux in general. But its really ATI's fault, the only reason nVidia works so well is because they invest a good amount of time in their drivers.

And to be honest even their Windows drivers are slightly lacking compared nVidia's Windows drivers.

~Jeff

---

### Post by baudday on 2009-11-03
Lol well I guess that's what I meant, I just phrased it wrong. That shouldn't happen since I'm taking a discrete mathematics class, but whatever haha. Anyway, thanks for the help. It looks like I'm going to have to use Windows for this one.

---

### Post by beastrace91 on 2009-11-03
> **baudday said:**
> I'm taking a discrete mathematics class

Oh that ones is always exciting... Wait till you get to analysis ;)

~Jeff

---

