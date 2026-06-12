---
title: "Install Different Versions of Wine"
date: 2009-07-07
forum: Wine
---

### Post by whatspaz on 2009-07-07
:guitar:
Hey guys! So last night I got bored and decided to work on this program idea I've been kicking around for a while. After hours of careful editing, I have a workable script that I am going to call "wine-age". The idea is simple, some wine is better if it is aged. ;) Now, where did I get this idea? It would seem some applications are broken in newer versions of wine (specifically, I'm having trouble installing Office 2007). I don't want to install an old version just for one program. Wow, what a dilemma! Alas, wine-age to the rescue. It will download files from here [http://wine.budgetdedicated.com/archive/index.html](http://wine.budgetdedicated.com/archive/index.html) and put them in a special folder here ~/.wine-age/. How nice!

How to use it:
1. Download it.
2. chmod +x it.
3. Run it under the terminal (don't elevate to root), use --help for command line options. Works almost like winetricks.
4. Check off the version you want/need/think you want/need. Click OK.
5. You can now run the installed version of wine.

Suspected issues:
o I wouldn't try it out under KDE/Qt. It may be broken, I don't have KDE to test it; so idk.

The wine versions will be installed at ~/.wine-age/. The wine executable files are installed at ~/.wine-age/*/usr/bin. The wine libraries are installed at ~/.wine-age/*/usr/{lib,lib32}.

So, for this to be useful, you will need to invoke the specific wine versions by setting some environment variables, see here: [http://www.winehq.org/site/docs/wine](http://www.winehq.org/site/docs/wine).

WINEPREFIX=<your wine prefix> \
WINESERVER=~/.wine-age/<version>/usr/bin/wineserver \
WINELOADER=~/.wine-age/<version>/usr/bin/wine \
32 bit:
WINEDLLPATH=~/.wine-age/<version>/usr/lib/wine \
*OR*
64 bit:
WINEDLLPATH=~/.wine-age/<version>/usr/lib32/wine \
~/.wine-age/<version>/usr/bin/wine \
<command line>

example:
WINEPREFIX=~/.wine \
WINESERVER=~/.wine-age/jaunty_wine1_1_25_amd64/usr/bin/wineserver \
WINELOADER=~/.wine-age/jaunty_wine1_1_25_amd64/usr/bin/wine \
WINEDLLPATH=~/.wine-age/jaunty_wine1_1_25_amd64/usr/lib32/wine \
~/.wine-age/jaunty_wine1_1_25_amd64/usr/bin/wine \
"Notepad.exe"

I think it should take some of the labor out of making new wine do old tricks. Your mileage may vary.

Peace Love Spaz!

---

### Post by cogadh on 2009-07-07
Not to rain on your parade, but there are already apps that do this, like PlayOnLinux, though it is nice to have something that just does this and no more.

---

### Post by demonccc on 2011-01-07
Thank you for the tip.

---

### Post by cipricus on 2013-02-19
As [cogadh]("http://ubuntuforums.org/member.php?u=48823") said, playonlinux should do it, i found this: [http://ubuntu.igameilive.com/2010/02/how-to-use-multiple-versions-of-wine-in.html](http://ubuntu.igameilive.com/2010/02/how-to-use-multiple-versions-of-wine-in.html)

---

