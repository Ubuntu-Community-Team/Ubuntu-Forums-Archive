---
title: "Steam won't launch games"
date: 2011-05-26
forum: Wine
---

### Post by JadeTigerVG on 2011-05-26
So, I've tried doing this before using winetricks, got the same problem

Used [http://cinderbox.net/2011/05/02/how-to-install-steam-in-ubuntu-11-04-a-game-distribution-platform/](http://cinderbox.net/2011/05/02/how-to-install-steam-in-ubuntu-11-04-a-game-distribution-platform/) this time to install steam

Got the same problem: Steam will launch the "preparing to launch" window, then will never launch the game. Any ideas?

---

### Post by JadeTigerVG on 2011-05-26
Hello? Have you given up?

---

### Post by WorMzy on 2011-05-26
Try launching the game from the command line with the [-applaunch <AppID>]("http://developer.valvesoftware.com/wiki/Steam_Application_IDs") flag for the steam executable.

It may give you some feedback on why the game isn't launching.

---

### Post by Elfy on 2011-05-26
Thread moved to Wine.

---

### Post by JadeTigerVG on 2011-05-26
It says there is no command found for -applaunch

---

### Post by WorMzy on 2011-05-26
How are you using it?

Your command should look something like this:
```
wine /path/to/steam.exe -applaunch 1234
```

---

### Post by JadeTigerVG on 2011-05-26
So, what? I don't know where the steam.exe file is, only the launcher

---

### Post by lightstream on 2011-05-26
Your path is most likely "C:\Program Files\Steam\Steam.exe" (you will need the quotes ")

Check [this page]("http://developer.valvesoftware.com/wiki/Steam_Application_IDs") to find the applaunch code for the Steam game you're trying to run.

---

### Post by JadeTigerVG on 2011-05-26
The code I want isn't there

EDIT: downloaded a different demo, trying to launch it now

---

### Post by JadeTigerVG on 2011-05-26
wine: cannot find 'C:\Program Files\Steam\Steam.exe'

Where else could it be?

---

### Post by WorMzy on 2011-05-26
> **JadeTigerVG said:**
> So, what? I don't know where the steam.exe file is, only the launcher

So, what? How is anyone else supposed to know where you installed it?

...is what I'd like to say, but chances are it got installed to "~/.wine/drive_c/Program Files/Steam/Steam.exe"

---

### Post by JadeTigerVG on 2011-05-26
I dont even know where I downloaded it. I used the how-to I posted in the first post, maybe that could help? I dont know how, but it might

---

### Post by JadeTigerVG on 2011-05-26
Found it. Forgot to mention theres a search function. Funny that. What popped up is attached

---

### Post by lightstream on 2011-05-26
That looks weird. I think what you've done is found some worker files created by the system for running programs (processes).

That is not the real location of the file.

If you go to your wine drive C, by typing **cd ~/.wine/drive_c** from a terminal, that is where your C: drive is located in wine - all Windows programs should be installed in a subdirectory off there.

Try using the command line **find** command from that location, like this:

[B]cd ~/.wine/drive_c
find . -name Steam.exe[/B]

---

### Post by JadeTigerVG on 2011-05-26
```
brandi@brandi-Extensa-5630:~$ cd ~/.wine/drive_c
brandi@brandi-Extensa-5630:~/.wine/drive_c$ find .-name Steam.exe
find: `.-name': No such file or directory
find: `Steam.exe': No such file or directory
brandi@brandi-Extensa-5630:~/.wine/drive_c$ 

```

Edit: Oops I forgot a space the first time

---

### Post by JadeTigerVG on 2011-05-26
Well I went into steam and I managed to launch insaniquarium and fish tycoon (both demos) but fish tycoon had no image, only sound, and it froze my computer

---

### Post by lightstream on 2011-05-26
I don't know about either of those games, but at least you got a bit further!

If you don't already know, the [Wine App DB]("http://appdb.winehq.org") is a good place to check out compatibility of games.

Good luck with it. I'm currently downloading Far Cry (bargain £1.25 on Steam today only!)

Edit: If you're using built-in netbook Graphics, you will be restricted on what games will run

---

### Post by JadeTigerVG on 2011-05-26
This isn't a netbook? its a stupid acer extensa...

---

### Post by lightstream on 2011-05-26
OK a regular laptop then, however it's just got integrated graphics (as opposed to a separate nvidia or ATI graphics card). Just be aware that you might not be able to run games with heavyduty 3D graphics etc. Your CPU doesn't look too bad though.

---

### Post by JadeTigerVG on 2011-05-27
Yeah. Think it'd run Terraria?

---

### Post by lightstream on 2011-05-27
haven't heard of that one before - just checked a YouTube video, looks cool, a bit like a sort of 2D minecraft with more spells and less mining (!)

I would think your hardware is ~capable~ of running it fine, but whether it'll run OK under WINE is another question...

Do you dual boot or are you a Linux-only Gamer(tm)? 

The game I just downloaded (Far Cry) doesn't seem to work for me under WINE so I'm having to boot into Windows to play it yukk

Gotta go to bed now, will probably be around tomorrow, see ya and good luck!

---

