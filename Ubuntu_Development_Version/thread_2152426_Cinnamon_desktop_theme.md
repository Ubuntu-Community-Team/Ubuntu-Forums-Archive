---
title: "Cinnamon desktop theme"
date: 2013-06-07
forum: Ubuntu Development Version
---

### Post by pfeiffep on 2013-06-07
Remains not functional - Anyone actually have it working?

Also I noticed that pdf printing to my HP results in a crash - apport captured it just fine!

---

### Post by pressureman on 2013-06-09
You're worried about the theme? I can't even get Cinnamon to work on Saucy. I've tried both the cinnamon-stable and cinnamon-nightly repos.

I'd like to get Cinnamon working on Saucy, since neither Unity nor GNOME Shell really fit my workflow. I like to test the latest dev changes, hence why I run Ubuntu Saucy.... were it not for that, I'd simply install Linux Mint 15.

---

### Post by shaun79 on 2013-06-09
Hi,

Are you using Saucy Salamander or Linux Mint? You're probably better off asking the Mint users here [http://forum.linuxmint.com/](http://forum.linuxmint.com/) for Cinnamon desktop help. Or if you're using Cinnamon desktop on top of Ubuntu then I'd go here [http://ubuntuforums.org/forumdisplay.php?f=329](http://ubuntuforums.org/forumdisplay.php?f=329)

For your problem with printing, have a look in the hardware sub-forum here? [http://ubuntuforums.org/forumdisplay.php?f=332](http://ubuntuforums.org/forumdisplay.php?f=332)

Good Luck!

---

### Post by pfeiffep on 2013-06-09
@[COLOR=#000000]pressureman - I really not worried about anything - saucy [/COLOR]):P[COLOR=#000000]is a test environment for me. For real use I'm using Ubuntu 13.04 with cinnamon desktop installed and really like it much better than Unity. An aside - I've installed LM 15 on my 2005 Dell laptop and find that cinnamon is fully functional there too!

@[/COLOR][COLOR=#000000]shaun79 - I'm using Suacy Salamander (Ubuntu 13.10) and installing the Cinnamon desktop theme. I have stable [/COLOR];) [COLOR=#000000]installations of Win 7, Ubuntu 13.10, Linux Mint 15. WRT printing, I'll just wait for a month or so to see if it's been fixed, if not then I'll take the time to report a bug.[/COLOR][COLOR=#000000]


[/COLOR]

---

### Post by pressureman on 2013-06-09
I'm running Ubuntu 13.04 at work with Cinnamon, and it works very nicely. At home I'm running Saucy with GNOME Shell (gnome3-team PPA, but that's probably not needed anymore as most of 3.8 has landed in Saucy).

After unsuccessfully trying to get Cinnamon to work on Saucy, I decided it best to continue my experimentation inside a VM. Cinnamon desktop fails to load, with the following logged to ~/.xsession-errors:

```

** Message: using fallback from indicator to GtkStatusIcon
    JS ERROR: !!!   Exception was: Error: No JS module 'dbus' found in search path
    JS ERROR: !!!     message = '"No JS module 'dbus' found in search path"'
    JS ERROR: !!!     fileName = '"/usr/share/cinnamon/js/ui/main.js"'
    JS ERROR: !!!     lineNumber = '47'
    JS ERROR: !!!     stack = '"@/usr/share/cinnamon/js/ui/main.js:47
"'
    JS ERROR: !!!   Exception was: Error: No JS module 'dbus' found in search path
    JS ERROR: !!!     message = '"No JS module 'dbus' found in search path"'
    JS ERROR: !!!     fileName = '"/usr/share/cinnamon/js/ui/main.js"'
    JS ERROR: !!!     lineNumber = '47'
    JS ERROR: !!!     stack = '"@/usr/share/cinnamon/js/ui/main.js:47
"'
Window manager warning: Log level 32: Execution of main.js threw exception: Error: No JS module 'dbus' found in search path

```

... at which point it loads the Cinnamon fallback mode (which looks very much like the old GNOME Panel).

I'm fairly sure I tracked it down to the fact that one of the (indirect) Cinnamon dependencies, libgjs0c, no longer includes dbus.js (since Saucy). This may be something that happened upstream, between libgjs 1.34 and 1.36.

---

