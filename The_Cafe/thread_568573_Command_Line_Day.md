---
title: "Command Line Day"
date: 2007-10-06
forum: The Cafe
---

### Post by blithen on 2007-10-06
What do you guys think about a command line day?
I'm talking about serious command line NO gui at all. Like alt+ctrl+f1 etc. stuff.
We had a chuck norris day, why not a CL day. I was thinking about next saturday?
Or do you guys hate this idea? I already use a CL music player. I've been using finch more and more, and as of right now I'm on w3m.

---

### Post by FuturePilot on 2007-10-06
How would you post anything?

---

### Post by blithen on 2007-10-06
Have you ever used w3m? It's very easy to use. Kinda time consuming but I have nothing better to do. 
I guess it was a stupid idea. I will however be using the command line on that day.

---

### Post by FuturePilot on 2007-10-06
Hmm. Never heard of it. Is it a text browser?

---

### Post by RAV TUX on 2007-10-06
are you using 9wm as your WM?


[[IMG]http://cafelinux.org/OptickleArt/albums/userpics/normal_snapshot15.png[/IMG]]("http://cafelinux.org/OptickleArt/displayimage.php?album=lastup&cat=0&pos=0")

---

### Post by tbroderick on 2007-10-06
> **FuturePilot said:**
> How would you post anything?

Elinks works fine with this forum and with gmail if you use that. Web 2 stuff is out of the question as is some secure sites like banks. Most popular websites have a mobile version which are suited well for cli browsers.

---

### Post by tbroderick on 2007-10-06
> **RAV TUX said:**
> are you using 9wm as your WM?


dwm is better.

Edit:
You should check out scrot instead of ksnapshot.

---

### Post by blithen on 2007-10-06
> **RAV TUX said:**
> are you using 9wm as your WM?


[[IMG]http://cafelinux.org/OptickleArt/albums/userpics/normal_snapshot15.png[/IMG]]("http://cafelinux.org/OptickleArt/displayimage.php?album=lastup&cat=0&pos=0")

Jeeze Rav you have tried waaay to many WM :P
I will defiantly give that a try though.

---

### Post by RAV TUX on 2007-10-06
> **blithen said:**
> Jeeze Rav you have tried waaay to many WM :P
I will defiantly give that a try though.
```

sudo apt-get install 9wm
```

---

### Post by RAV TUX on 2007-10-06
> **tbroderick said:**
> dwm is better.

Edit:
You should check out scrot instead of ksnapshot.I have never heard of scrot. What's better about scrot?

---

### Post by blithen on 2007-10-06
> **RAV TUX said:**
> ```

sudo apt-get install 9wm
```
w00t.
Thanks. Oh by the way. Awesome Avatar.

---

### Post by RAV TUX on 2007-10-06
> **blithen said:**
> w00t.
Thanks. Oh by the way. Awesome Avatar.Thanks, and Good Welcome.

---

### Post by MRiGnS on 2007-10-06
These are all TUI browsers, I doubt there even are CLI browsers hence it would be just stupid.

[TUI]("http://en.wikipedia.org/wiki/Text_user_interface") vs [CLI]("http://en.wikipedia.org/wiki/Command_line_interface")

---

### Post by tbroderick on 2007-10-06
> **RAV TUX said:**
> I have never heard of scrot. What's better about scrot?

Ksnaphot seems out of place in a light weight window manager. Scrot doesn't have the large dependencies.

---

### Post by Celegorm on 2007-10-06
I'd love to join in. I'm always trying to learn how to do more things through the command line. The only thing I'm hesitant about is sites that don't play nicely with CLI browsers (I don't suppose any exist that can handle javascript or flash?) Anyway, it's not a big issue for just a day, but there's a website I have to use for school that I haven't gotten to play nicely with a CLI browser yet, largely because it forces a check to make sure popups are allowed before I can log in (which annoys me to no end when I have to log in to download files for an assignment and I'm using ssh with no X).

---

### Post by blithen on 2007-10-06
> **Celegorm said:**
> I'd love to join in. I'm always trying to learn how to do more things through the command line. The only thing I'm hesitant about is sites that don't play nicely with CLI browsers (I don't suppose any exist that can handle javascript or flash?) Anyway, it's not a big issue for just a day, but there's a website I have to use for school that I haven't gotten to play nicely with a CLI browser yet, largely because it forces a check to make sure popups are allowed before I can log in (which annoys me to no end when I have to log in to download files for an assignment and I'm using ssh with no X).

W00t two people. That's awesome. Thanks for joining.

---

### Post by Celegorm on 2007-10-06
I can't get mplayer to play movies in the ctrl-alt-f1 terminal (though it works fine if I pick failsafe terminal at the login screen). Which brings up the question: is this more of a challenge to go a whole day without X or just a whole day without touching anything but a command line? If it's the latter I might use [GNU screen]("http://www.gnu.org/software/screen/") as a wm and then just not use any apps that can't be run from, and in, an xterm. If it's the former, I think I'll be playing a lot of nethack that day :cool:

---

### Post by Frak on 2007-10-06
Hey RAV, have you tried SWM?

Also, CLI day would be great!

---

### Post by IYY on 2007-10-06
Some tips:

**mocp** as the music player (sudo apt-get install moc)
**centericq** or **finch** as the instant messanger
**midnight commander** (mc) as the file manager if you need one
**bitchx** as the IRC client
**imagemagick** (use the 'convert' command) to do image manipulation like resizing, conversion, cropping, etc.
**vi** as the text editor
**python** as the calculator. No, seriously -- the easiest and most robust commandline calculator is python. Just enter the python shell and type in an expression, and it will be evaluated.
**LaTeX** to typeset documents (you'll end up with a PDF that looks much better than anything created with Word).
**antiword** to read .doc files in ASCII.

---

### Post by Stuart Morrow on 2007-10-31
> **IYY said:**
> 
**python** as the calculator. No, seriously -- the easiest and most robust commandline calculator is python. Just enter the python shell and type in an expression, and it will be evaluated.

Absolutely. Even in GNOME and KDE, I use Python as my calculator.  So anyway, I just wanted to add that "_" in the interactive shell works as a kind of "the value of the last calculation" variable.  Treat it as read-only, though; DO NOT ASSIGN A VALUE TO IT.

Trig functions, logs, whatever else, can be imported like so:

import math  # sin for example would now be accessed like "Math.sin(theta)"
# or,
from math import sin # sin for example now would simply be "sin(theta)"

Yeah, I just wanted to mention that useful "_" thing (because so many people read this thread (!))

---

