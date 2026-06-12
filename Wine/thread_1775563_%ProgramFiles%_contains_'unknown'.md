---
title: "%ProgramFiles% contains 'unknown'"
date: 2011-06-04
forum: Wine
---

### Post by ve4cib on 2011-06-04
I've never used Winetricks before, but on a whim I decided to click on the Applications>Wine>Winetricks item just to see what it would do.

Apparently it does nothing.

Running $ winetricks --gui gives me this error message:

> wine cmd.exe /c echo '%ProgramFiles%' returned a string containing the word 'unknown', as if a voice had cried out in terror, and was suddenly silenced.

Executing the command mentioned in the error message give me this:

> C:\windows\system32\unknown

I've been running into little glitchy problems with every program I try to install using Wine trying to install to drive_c/system32/unknown, so I'm guessing this winetricks problem is related.  I've never bothered trying to fix the default install directory before, so I'm not even sure where to begin.

Anyone have any suggestions for commands to run?  I know basically nothing about Wine other than it lets me play Diablo and Age of Empires.

Some extra information, in case it's needed:

OS: Ubuntu 11.04
wine --version: wine 1.2.2
winetricks --version: 20110402

---

### Post by cwwilson721 on 2011-06-04
From your errors, I'll have to assume you haven't installed anything in wine, correct?

If this is true, let's just start from the beginning. I'll assume you installed wine already.

[COLOR="Blue"]NOTE: The following is a VERY basic wine install how-to., and to get winetricks working. This is NOT a how-to on installing a specific game, or how-to make different wine prefixes.[/COLOR]

First, check and see if you have a '.wine' folder in your home folder. (If using Nautilus, click View > Show Hidden). 

If you do have a .wine folder, delete it.

Next, from a terminal, type ```
winecfg
```and press 'enter'. This will create your '.wine' folder, needed'windows folders', required basic dll's, and a registry. It also sets up the Gecko engine (If it asks you to do so, say "yes"), and your audio drivers (Go to the Audio tab, and select "Alsa")

NOW you should be able to use winetricks to install some extra stuff. Just type ```
winetricks
```in a terminal, it will start a GUI by itself.

---

### Post by ve4cib on 2011-06-04
I've installed several programs in Wine.  However, all of the installers defaulted "C:\Windows\System32\unknown" and I had to manually change the path to "C:\Program Files" when installing them.  After running the installer the programs all work fine.  (e.g. Diablo II, Dawn of War, Age of Mythology, and a handful of other games.)

My wine directory is $HOME/.wine, as normal, and contains the standard assortment of files and directories one would expect:

```

$ ls .wine
user.reg  userdef.reg  system.reg  drive_c  dosdevices

$ cd .wine
$ ls drive_c
Program Files  users  windows

```

In winecfg I have three drives mapped:

C: "../drive_c"
D: "/media/cdrom"
E: "/home/*username*" (where username is my username, obviously)

---

### Post by cwwilson721 on 2011-06-05
Okay. So try renaming your .wine folder, running winecfg, then winetricks, then install something, and see if it gets it straight.
If so, then it may have been an issue when you first started with wine, and it borked the install.

Give it a shot, won't hurt anything. You can always rename the renamed wine folder back to '.wine'

---

### Post by Dakiraun on 2011-08-16
I ran into this as well.  The problem is caused by something in WINE renaming Program Files references in the system.reg file to "C:\\windows\\system32\\unknown".

You can fix the issue by changing them back to what they should be.  First, open a terminal and type "[COLOR="Indigo"]**wineboot -s**[/COLOR]" to shutdown any instance of WINE.  Obviously, close your programs and save stuff first.

Then use an editor like **[COLOR="DarkGreen"]gedit[/COLOR]** to open the [COLOR="Indigo"]**system.reg**[/COLOR] file located in **[COLOR="Indigo"]~/.wine[/COLOR]**.  In gedit (or whatever editor you wish to use) do a Search/replace and replace any instance of "[COLOR="Indigo"]**C:\\windows\\system32\\unknown**[/COLOR]" with "[COLOR="Indigo"]**C:\\Program Files**[/COLOR]".  This gets winetricks working again.

In the terminal, type "[COLOR="Indigo"]**wineboot**[/COLOR]" to restart WINE.

The only issue is, I don't know what causes this to happen, so there is always the chance it could get corrupted again.  At least it can be fixed.

---

