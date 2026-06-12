---
title: "Wine Unbearably Slow"
date: 2009-08-02
forum: Wine
---

### Post by MrDelish on 2009-08-02
After using Wine without any significant hitches for over a year, I've just come across one. I've been running Jaunty on my dual-core Dell desktop with 4GB of RAM for about a month now, and Wine is getting slowed down by... something. I installed AWN and some other fun stuff recently, but nothing I would imagine would interfere with Wine. Every time I load any application (even winecfg), it takes between thirty seconds to one minute for it to load. During this time, normal functions take forever or don't work at all (selecting folders, opening a file, etc.). Sometimes it will load and work just fine, but often the program continues to wreak havoc by slowing down the system for as long as five minutes after closing the program. Per threads such as [this one]("http://ubuntuforums.org/showthread.php?t=1206179"), I've attempted the following:

- Upgraded Wine version from 1.1.24 to 1.1.26
- Changed a bunch of things in winecfg - OS emulation, disabled audio, unchecked the boxes for allowing the window manager to control the windows, emulated virtual desktop, yadda yadda...
- Removed old software and some folders created during an attempt to get DirectX working in Wine
- Disabled all desktop effects

Needless to say, the problem persists. I do have a list of DLL overrides (these didn't cause a problem before, but I can remove them if they could be part of the problem). I'm not sure what else to look at or try, but any suggestions will be appreciated as I love me some Wine... :KS

---

### Post by NightMKoder on 2009-08-02
Some program probably installed some device/service that doesn't work correctly. There's really no clean way to resolve it - it's best to just start over with a clean wine prefix. For future reference, you can install applications to different wine bottles - that way when something is messed up in one bottle the others are unaffected (google wine bottle).

---

### Post by MrDelish on 2009-08-03
Looking into that option right now, and it sounds like a plan. I'm surprised I've been able to use it so much without any serious problems until just now.

I found [this tutorial]("http://linux-tipps.blogspot.com/2009/03/how-to-make-your-own-wine-bottles.html"), but is there any better/easier method of setting Wine bottles up?

---

### Post by NightMKoder on 2009-08-03
There are a few. Here's a list of easiest to hardest: 
1. Crossover
2. PoL
3. Start installers with ```
WINEPREFIX=/home/$USER/.wine_bottles/bottle_name wine Setup.exe
```
4. That script.

---

### Post by MrDelish on 2009-08-04
Thanks very much for the help and suggestions so far, NightMKoder.

During my uninstallation rampage I took out PlayonLinux, reinstalled it, then set up a basic code editor I like to use in its own prefix (PSPad - [http://www.pspad.com/](http://www.pspad.com/)). That still seems to be going much slower than usual, so is there a step I could have missed when setting this up? I cleared out the existing ~/.wine directory and checked to sure I have a separate directory (/home/USER/.PlayOnLinux/wineprefix/PSPad) for the application, so it seems like this should be fresh. Maybe I'm just too impatient... :P

---

### Post by MrDelish on 2009-08-04
Still not getting anywhere... I ran the following commands

```
sudo apt-get remove wine
rm -rf $HOME/.wine
rm -f $HOME/.config/menus/applications-merged/wine*
rm -rf $HOME/.local/share/applications/wine
rm -f $HOME/.local/share/desktop-directories/wine*
rm -f $HOME/.local/share/icons/????_*.xpm
```

along with wiping out my ~/.wine and ~/.PlayOnLinux directories, went through Synaptic and installed v 1.0.1, then opened up Notepad to test. Same problems as before; it takes a good minute before it loads and then everything slows down to a snails pace, regardless of the presence of desktop effects.

Any advice from here?

---

### Post by diagram30 on 2009-08-05
Are you using a 64-bit OS?

---

### Post by MrDelish on 2009-08-05
Yep, it's 64-bit Jaunty. Sorry I didn't mention that earlier.

---

### Post by MrDelish on 2009-08-06
I guess now would be a good time to scrap my entire installation and give Kubuntu a try, though it seems odd that Wine would be so temperamental all of a sudden. Would it be better to stick with a 32-bit version or does it make any difference with Wine?

---

