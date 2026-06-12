---
title: "Switch windows version via cmd line?"
date: 2009-01-19
forum: Wine
---

### Post by FrozenFox on 2009-01-19
Hellos. An extremely simple question here.. 

A game I'm trying to play won't work under XP mode, which I wish to use in general, but works flawless under windows 98 mode.

After looking around for 20 minutes on the web, and scrolling around through the manual page, I can't seem to find a way to make this happen with any remotely modern version of wine. Anyone know how I might do it? Or perhaps have a quick script to switch out the line accordingly in the config file wine saves this at? Am I completely blind and skimmed over it somewhere? This seems like something that should be as simple to do as wineprefix..

Using winecfg to fix this every time is pretty annoying. Solutions?

---

### Post by yther on 2009-01-19
Interesting question... OK, if I'm reading this correctly, it should be possible.  [Documentation]("http://www.winehq.org/docs/wine") at WineHQ for environment variables says:

```
WINEPREFIX
              If set, the content of this variable is taken as the name of the
              directory where wine stores its data (the default is $HOME/.wine
              ).  This  directory is also used to identify the socket which is
              used to communicate with the  wineserver.   All  wine  processes
              using the same wineserver (i.e.: same user) share certain things
              like registry, shared  memory,  and  config  file.   By  setting
              WINEPREFIX  to different values for different wine processes, it
              is possible to run a number of truly independent wine processes.

```

Based on this, you should be able to set up two separate directories, for example ~/.winexp and ~/.wine98; the files in each would be set to provide whichever Windows version you need.

Then when you run the app (from an alias or program icon), do something like this:

```
export WINEPREFIX="$HOME/.wine98" wine "c:\blah.exe"
```

I believe that should work.

---

### Post by cogadh on 2009-01-19
There's a much easier way to do it. Just create an application profile for the executable in winecfg and set the Windows version to Windows 98. That way even if Wine has XP set as the default Windows version, it switches to 98 when that executable is run.

---

### Post by yther on 2009-01-19
Oh yes, that sounds much easier! 

Can you tell I don't use WINE often?  ;)

---

### Post by FrozenFox on 2009-01-20
Cogadh:

Thank you, that will do exactly what I'm looking for. I was about to ask for help again because it wasn't working, but as I started typing it, the solution dawned on me. Apparently, setting an app profile for an exe does not transfer over to apps that exe calls.

Ie if you want to run a game win98 mode using a launcher, all exe's that it would call need their own profile, it doesn't automatically chain.

Ty as well yther :)

PS: Wth, 'mark as solved' doesnt appear to be under thread tools anymore.. Where is it now? o.O

---

### Post by cogadh on 2009-01-20
A few things are missing since they did that last "database maintenance". I'm sure it will come back eventually.

---

