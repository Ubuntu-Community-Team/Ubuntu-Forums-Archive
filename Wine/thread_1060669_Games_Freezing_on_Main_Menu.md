---
title: "Games Freezing on Main Menu"
date: 2009-02-05
forum: Wine
---

### Post by Infamshxr on 2009-02-05
I installed Call of Duty: Game of the Year Edition and Star Wars: Jedi Academy. Both installed with little problems, but Every time I go to play either game, the Main Menu pops up with the options of Single Player, Multiplayer, Options, etc, but whenever I click any of the options it the program stops responding and turns gray for some reason... Any ideas? I haven't a clue why it's doing that, especially since wineHQ says both games are supposed to work great.

---

### Post by cogadh on 2009-02-05
Wine version? Ubuntu version? Hardware specs?

Also it would be helpful if you tried running the game from the terminal, then posting the output here. It may contain error messages that explaiun exactly what is going on.

---

### Post by Infamshxr on 2009-02-05
I just installed the current version of wine, according to winehq, it's 1.0.1 I know it's that one cuz I installed it last night. (I'm not home right now... lol)

As for my computer, here are my specs:

Acer Travelmate 2400
Ubuntu 8.04 (running compiz, beryl, and screenlets too)
Intel Celeron 1.46 GHz
1408 MB RAM (cuz of shared video memory)
ATI Radeon 200M (set at 128 MB)
40 GB HDD
CD-Burner/DVD-ROM (24x, I think)

I'll get back to you with the output on the terminal when I get the chance. Probably tonight or tomorrow. Thanks for the help so far.

---

### Post by cogadh on 2009-02-05
Right off the bat, I already see a problem. Wine does not get along with Compiz/Beryl/Desktop Effects. Before running any game in Wine, you need to disable that completely and restore Metacity as the window manager.

---

### Post by Infamshxr on 2009-02-05
Oh... That would explain some problems lol. Is there any special way I am supposed to do that or just go into Control Center > Appearence > Visual Effects and set it to off?

---

### Post by cogadh on 2009-02-05
There is a Compiz manager package you can install that places a shortcut on the system dock which allows you to right-click on it and switch to Metacity on the fly. Unfortunately I am not at my Ubuntu machine right now, so I can't check for the actual name of the package. If you search through Synaptic, it should be relatively easy to find.

---

### Post by Infamshxr on 2009-02-05
Don't worry, I know what you are talking about. I'll try it when I get home later tonight and let ya know how it goes.

---

### Post by Infamshxr on 2009-02-06
Well, I wasn't able to test the two games quite yet, but I did install C&C Renegade. It runs, but runs kinda crappy. Overall good though. Is there something I can do about the jittery mouse or my extremely high ping of like 150ish? If those two things are fixed I don't think I can complain.

---

### Post by Infamshxr on 2009-02-07
bump... Any ideas?

---

