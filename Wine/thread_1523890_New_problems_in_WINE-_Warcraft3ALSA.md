---
title: "New problems in WINE- Warcraft3/ALSA"
date: 2010-07-04
forum: Wine
---

### Post by Peter7K on 2010-07-04
Hello, I am running Lucid 10.04 Ubuntu, with the latest dev package in the repository of WINE.

My first problem is WINE not recognizing the ALSA driver.  When I do winecfg, go to audio, 
"Found  driver in registry that is not available!

Remove 'alsa' from registry?"

It's worked fine for a year and a half now, I don't know why it has started malfunctioning now.  It continues to do this after I have done a full complete removal and reinstall of WINE as well (though I guess the installed programs remain..?)

Second, Warcraft 3 will no longer run.  I get Error: "Couldn't open Game.dll."

```
$ wine start /Unix "/home/peter/.wine/drive_c/Program Files/Warcraft III/war3.exe" --opengl
$ err:ole:CoCreateInstance apartment not initialised
err:module:import_dll Library OPENGL32.dll (which is needed by L"C:\\Program Files\\Warcraft III\\Game.dll") not found

```

This continues after I have also reinstalled Warcraft 3 completely as well.  Both ALSA and Warcraft 3 have been running flawlessly for the past 1.5-2 years on my system.  Any thoughts or possible fixes?  Thank you for your time.

EDIT: Discovered that I had not uninstalled a self compiled version of wine that was causing these issues.

---

