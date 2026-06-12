---
title: "Console Only Distro"
date: 2009-03-01
forum: The Cafe
---

### Post by Woodsyx on 2009-03-01
I remember seeing screenshots of someone running a distro that split the screen into 4 console instances but I can't remember what he was running. Does anyone know if that's possible with Ubuntu or any other Distro or was I just seeing 4 open console windows and have a poor memory.

---

### Post by kk0sse54 on 2009-03-01
You mean something like [**_Screen?_**]("http://upload.wikimedia.org/wikipedia/commons/7/72/GNU_Screen.png"). You can also easily make a commandline only environment out of pretty much any distro.

---

### Post by namegame on 2009-03-01
For a "strictly CLI" distribution you could install Arch without X, Ubuntu-minimal, or something else like that. You could also look into INX, it's a LiveCD that is strictly CLI.

It could have been a distribution running a tiling window manager as it's "DE"

Examples include, dwm, awesome, and xmonad.

Any distribution can run these.

---

### Post by Bölvaður on 2009-03-01
I use awesome + vimperator plugin for firefox on my laptop, and it is so great :). The only problem with that is that wireless isn't automatically detected, but a short script fixed that (and connects way faster).

Tiling window managers are not cli only, as you can guess from me having firefox it just manages the windows differently, are very light and are more powerful with the commandline than GNOME imo.

---

### Post by cookieofdoom on 2009-03-01
If you're going CLI only I recommend OpenSUSE. You can use screens with it (it's probably in the repos, I don't know, though), and it's got an amazing configuration manager for the command line called "YAST". Just run yast from the command line.

Arch boots faster, and if you know Linux well it can be a better option.

---

### Post by MaxIBoy on 2009-03-01
Are you talking about something like this?
[IMG]http://arch.kimag.es/resized/88685096.png[/IMG]
This is an X window manager. It's a lot like the one you probably currently use, but it's designed to let you "tile" the windows. Often, people use them to tile a lot of terminals.




Or this?
[IMG]http://upload.wikimedia.org/wikipedia/commons/thumb/7/72/GNU_Screen.png/684px-GNU_Screen.png[/IMG]This actually is running in full textmode, x11 isn't being run at all. You don't even need a graphics card at all to use one of these. However, these are more useful if you use a framebuffer to increase the resolution past 80 lines and 25 characters per line.

---

### Post by Woodsyx on 2009-03-01
> **MaxIBoy said:**
> Are you talking about something like this?
[IMG]http://arch.kimag.es/resized/88685096.png[/IMG]
This is an X window manager. It's a lot like the one you probably currently use, but it's designed to let you "tile" the windows. Often, people use them to tile a lot of terminals.




Or this?
[IMG]http://upload.wikimedia.org/wikipedia/commons/thumb/7/72/GNU_Screen.png/684px-GNU_Screen.png[/IMG]This actually is running in full textmode, x11 isn't being run at all. You don't even need a graphics card at all to use one of these. However, these are more useful if you use a framebuffer to increase the resolution past 80 lines and 25 characters per line.

I was thinking of something more along the lines of the first screenshot. So one of the packages listed on this site? [http://xwinman.org/](http://xwinman.org/)

Any recommendations on whats better/less bugs/something else...

---

### Post by adamlau on 2009-03-01
Any distro with a tiling WM will do what you are asking (which is not distro specific).

---

