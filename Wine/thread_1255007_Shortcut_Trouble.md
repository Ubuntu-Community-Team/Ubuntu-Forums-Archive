---
title: "Shortcut Trouble"
date: 2009-08-31
forum: Wine
---

### Post by Fernando Hernandez on 2009-08-31
Hello.  

I've been using Kubuntu for a few months, now, and loving it.  I'm enjoying WINE, as well, for the few programs I need to run under it have no trouble.  However, I recently installed a game and to run the English patch I need to run a file called onscripter.exe.  It runs fine if I navigate to the folder and run the .exe file directly, but I can't create a shortcut that properly launches the program.

I've gone into my menu editor and set up a shortcut to the .exe file but all it does is run the busy icon for a few seconds and then stop, as nothing happens.  Is there a way around this?  It's a pain to have to navigate all the way to the folder to run it, and I'd really like to have a working shortcut in my Kickoff menu.

Oh, and if it involves using the command line, please be as explicit as possible.  I'm still something of a n00b when it comes to the terminal, so dumb it down for me as best as you can.  :)

---

### Post by Dark Aspect on 2009-09-01
> **Fernando Hernandez said:**
> Hello.  

I've been using Kubuntu for a few months, now, and loving it.  I'm enjoying WINE, as well, for the few programs I need to run under it have no trouble.  However, I recently installed a game and to run the English patch I need to run a file called onscripter.exe.  It runs fine if I navigate to the folder and run the .exe file directly, but I can't create a shortcut that properly launches the program.

I've gone into my menu editor and set up a shortcut to the .exe file but all it does is run the busy icon for a few seconds and then stop, as nothing happens.  Is there a way around this?  It's a pain to have to navigate all the way to the folder to run it, and I'd really like to have a working shortcut in my Kickoff menu.

Oh, and if it involves using the command line, please be as explicit as possible.  I'm still something of a n00b when it comes to the terminal, so dumb it down for me as best as you can.  :)

Yeah it involves command line,

```
env WINEPREFIX="/home/{USERNAME}/.wine" wine "C:\Program Files\{APP.exe}"
```

Or if you installed the application in the default wine directory and the above is confusing, you could probably get away with

```
wine /home/{USERNAME}/.wine/drive_c/Program Files/{APP.exe}
```

---

