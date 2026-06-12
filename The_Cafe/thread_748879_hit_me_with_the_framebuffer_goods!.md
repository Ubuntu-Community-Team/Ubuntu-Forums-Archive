---
title: "hit me with the framebuffer goods!"
date: 2008-04-07
forum: The Cafe
---

### Post by chucky chuckaluck on 2008-04-07
ok, so i read a bunch of stuff on this framebuffer thing and have as good of an idea as i'll ever have what it is. as i understand it, it's something i have to enable in gutsy, yes? so, what's the best way to do it? even more importantly, what are its uses? what are its relative merits? is there a traditional frambuffer vs. x war i could be in danger of restarting? (all random thoughts are welcome.)

---

### Post by init1 on 2008-04-07
Framebuffer is a way to run graphical programs without X. One example is links2 -g. The advantage is that it doesn't use as much RAM as running an X session would. One would use a framebuffer app if they didn't have X installed (framebuffer apps may require X lib though).

---

### Post by original_jamingrit on 2008-04-07
[http://dev.gentoo.org/~spock/projects/fbcondecor/](http://dev.gentoo.org/~spock/projects/fbcondecor/)
fbdecor is a way to wallpaper your tty consoles.  Gentoo uses it, and Vector Linux (Slackware deriv) uses it or something similar.

[http://linux.bytesex.org/fbida/](http://linux.bytesex.org/fbida/)
fbida is a way to view images and pdf files from tty.

and you're supposed to be able to use mplayer like this to.

I'm just not sure how to use them in Ubuntu, but I guess if you download the necessary packages, you can get more instructions.

---

### Post by FuturePilot on 2008-04-07
> **original_jamingrit said:**
> [http://dev.gentoo.org/~spock/projects/fbcondecor/](http://dev.gentoo.org/~spock/projects/fbcondecor/)
fbdecor is a way to wallpaper your tty consoles.  Gentoo uses it, and Vector Linux (Slackware deriv) uses it or something similar.

Darn! Too bad you have to recompile the kernel to use that. I would love something like that. Mandriva 2008 has a nice background on the ttys

---

### Post by encompass on 2008-05-11
> **original_jamingrit said:**
> [http://dev.gentoo.org/~spock/projects/fbcondecor/](http://dev.gentoo.org/~spock/projects/fbcondecor/)
fbdecor is a way to wallpaper your tty consoles.  Gentoo uses it, and Vector Linux (Slackware deriv) uses it or something similar.

[http://linux.bytesex.org/fbida/](http://linux.bytesex.org/fbida/)
fbida is a way to view images and pdf files from tty.

and you're supposed to be able to use mplayer like this to.

I'm just not sure how to use them in Ubuntu, but I guess if you download the necessary packages, you can get more instructions.

Yeah... 
```
mplayer -vo fbdev videoFile.mpg
```
You can do alot of tweaking here and fortunately ubuntu has console help so you can use tab to fine the command line options and EVEN the drivers to you can try out.
for example fbdev2 and aa or the wonderful caca.
Have fun!

---

