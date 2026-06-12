---
title: "Counter Strike: Source graphics problem"
date: 2009-01-18
forum: Wine
---

### Post by timboos on 2009-01-18
Thanks in advance to anyone who can help me out with this problem. I recently switched my computer over from vista to Intrepid, and I would like to avoid having to do a dual boot by playing my favorite games on Ubuntu. I got counter strike: source working using this guide: [http://ubuntuforums.org/showthread.php?t=304528](http://ubuntuforums.org/showthread.php?t=304528).

First of all, the fonts are pretty messed up, the steam friends, in-game console and some other fonts are unreadable. I have the tahoma font downloaded but I can't find the correct folder to put it in. I don't know if that's the problem with the fonts...

I am able to play using ```
cd ~/.wine/drive_c/Program\ Files/Steam && WINEDEBUG=-all wine steam -applaunch 240 -dxlevel 90 -console
```

The only problems I'm experiencing is the occasional lag that I never got with vista, but the graphics are much worse than with vista. Most of the textures are ok, but the resolution or something isn't right - it just isn't as sharp as when I ran it on vista. I have the correct nvidia driver installed. I read somewhere that you can't get good graphics with linux because counter strike: source is directx based. I would really like the be able to fix this graphic problem. Here are my specs:

 I'm running a Dell XPS M1710 
Core 2 Duo 2.16 processor
Nvidia Geforce Go 7900 gtx 512 mb graphics card
2 GB Ram

Thanks for reading,
Timboos

---

### Post by timboos on 2009-01-20
bump

Can anyone help me out?

---

### Post by Frak on 2009-01-20
When in doubt, [Winetricks]("http://wiki.winehq.org/winetricks") or [Winedoors]("http://www.wine-doors.org/wordpress/").

Winetricks will help with the font issue, Winedoors should do the job for you.

---

### Post by timboos on 2009-01-23
I tried Wine tricks but I couldn't figure out what to do with wine doors. Wine tricks kind of helped my font issue (mostly fixed it but there's still a few things that are weird) but the graphics are still not what they were when I ran CS:S on Vista. Although it is playable, I play competitively so good graphics are a necessity for me. I would really like to avoid having to do a dual boot with Vista because I hate it. Any other suggestions?

---

### Post by Frak on 2009-01-23
Assuming you're running it from Steam, try right clicking on CS:S, go to properties, then "Set Launch Options" and entering "-dxlevel 81" (without quotes) and pressing ok.

You may be having DX9 issues.

---

### Post by ngrieb on 2009-06-05
I'm experiencing a high lag whenever an enemy crosses my line of sight (kind of like the game is taking too long to process), which makes for some pretty lame game play. If I am alone in a room running around the fps seems normal. I am running CS:S in dxlevel 81 mode, but have not turned off WINE error logging (would it make that big of a difference?). Does anyone have any ideas what I can do to make this stop?
Thanks in Advance.

Specs:
Ubuntu 8.10
Radeon X1650 Pro
1MB RAM
AMD Athlon 3000+
DLink DWL650? (Atheros Chip)

---

### Post by MysteriousKnight on 2009-06-14
Timboos, if you have an windows install handy(even on other pc) go to the windows folder on the c: drive and go to "fonts" folder, copy the fonts you want into your wine virtual c:drive in the windows folder, that should clear up the hard reading for you in steam and css.

Mk

---

### Post by MysteriousKnight on 2009-06-14
I also found a frame rate increase when i configure wine to run windows 2000, lol, oh and **disable** the steam in game in your steam options.

But please can anyone help, i really want to play it with better settings, its al its lowest now, and the frame rate is just playable. Used to play on high in windows.

Running nvidia 8600GT
3GB DDR2 800 RAM
AMD X2 5200+ 2.7GHz

---

