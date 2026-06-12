---
title: "How do I use tilda??"
date: 2006-07-05
forum: The Cafe
---

### Post by slimdog360 on 2006-07-05
I just read on an earlier post about tilda, I installed it through the repositories but I can only get it to run when I use a terminal and type 'tilda' into it, which defeats the purpose.
How do I get it run run when I press the ` key.
thanks

edit: sorry, I just realised I probably should have put this in the general section or something.

---

### Post by scxtt on 2006-07-05
i'm pretty sure it defaults to using F12 ... you can configure it by right-clicking on the tilda screen and set it to something else (via preferences and the keybindings tab) - tho i'm not sure ~ or ` will actually work ... i use the "windows logo" key myself ...

---

### Post by NESFreak on 2006-07-05
open tilde and rightclick-->preferences-->keybindings

---

### Post by slimdog360 on 2006-07-05
nope doesnt want to work

---

### Post by scxtt on 2006-07-05
what, specifically, "doesn't want to work"?

---

### Post by slimdog360 on 2006-07-05
when I change the key bindings, then use the key it doesnt work. But dont worry about it now its about 1:30am here, Ill figure it out in the morning. Thanks for the replies though.

---

### Post by NESFreak on 2006-07-05
run it  tru alt+F --> tilda
show and hide it with F1
change settings rmouse-->settings (from tilda)

you can add it to your startup apps (but then you should deselect 'display pulled down on start"

thats it

NESFreak

(i also can't figure out what the names of the keys are)

---

### Post by aroyce on 2006-08-28
Hi,

I think I'm having the same problem.
I configured it, and set the keybinding to F12, but it only works if I first
open a terminal window from Applications-->Accesories--Terminal and type 'tilda' and then leave that window open. If I close the original window, I can't access the tilda dropdown with F12 (or any other keybinding). I've tried adding it to my startup list (System-->Preferences-->Sessions-->Startup-->Add-->Tilda) but that doesn't seem to work.

any thoughts?

---

### Post by scxtt on 2006-08-28
tilda has to be running for it to work w/ your keybinding ... when i used it, i had created a launcher for it and added it to my menu ... then anytime i hit the "windows key" on my keyboard, i got tilda :) - of course if i exited the tilda shell, the windows key was once again worthless ...

---

### Post by replicant on 2006-09-04
what did you tell it in the keybindings to use for "windows key"?

---

### Post by scxtt on 2006-09-04
don't remember off the top of my head - it wasn't hard ... i vaguely remember just pressing it and letting it fill in whatever value was necessary ... it also requires some default keybinding to be in there as well (don't remember what that is) ... i don't feel like installing tilda again cause i'm using KDE and it'll install a lot of other stuff i don't need ...

---

### Post by rohan! on 2006-09-04
i love tilda, use it all the time, so don't give up yet...

i use fluxbox and just had to enter it into my .fluxbox/startup file, so i assume that with all you gnomers that you go to system>preferences>session and add it to your startup file. don't know exactly

also if you running in terminal put an & at the end (ie. ```
tilda & 
``` ) then you can close the terminal, because tilda will be running independent of it. or you could altF2 and type tilda to get it running.

(ps. i'm a little bit inebriated, so sorry if this is worthless advice!)

---

### Post by The Uniphobiac on 2006-09-04
I set the binding to "windows logo" by using None+Super_L

---

### Post by giosue_c on 2006-09-05
Looking here tells you what you need to do to use the ~ key or a few other things as the shortcut.

[http://tilda.sourceforge.net/wiki/index.php/Install_Guide](http://tilda.sourceforge.net/wiki/index.php/Install_Guide)

---

### Post by iblis on 2006-10-08
> **giosue_c said:**
> Looking here tells you what you need to do to use the ~ key or a few other things as the shortcut.

[http://tilda.sourceforge.net/wiki/index.php/Install_Guide](http://tilda.sourceforge.net/wiki/index.php/Install_Guide)
this site keeps on timing out for me;  however,  the README (located at /usr/share/doc/tilda on my installation) has some examples to get you started.  i was able to get it to work using None+grave (`),  and Shift+grave (~),  however since i used those keys a lot,  i opted to set it to Control-F1 instead.

hope this helps. :mrgreen:

---

### Post by Arkitekt on 2006-11-24
anyone know the command to add it to your start up?

---

### Post by argie on 2006-11-25
> **Arkitekt said:**
> anyone know the command to add it to your start up?
Yeah. In Dapper: System -> Preferences -> Sessions -> Startup Programs

Then just click "Add" and type in "tilda"

---

### Post by Dr4rchangel on 2007-06-20
I wanted to use the Keys Ctrl+\ (Backslash) to use Yakuake and wanted to use them again on tilda.
Anyone knows how I can set the Backslash on tilda keybindings? I tried backslash, bslash, \, \\, but it didn't work. And the install guide only has a '~' example :(

---

### Post by parthibanbls on 2009-03-01
> **Dr4rchangel said:**
> I wanted to use the Keys Ctrl+\ (Backslash) to use Yakuake and wanted to use them again on tilda.
Anyone knows how I can set the Backslash on tilda keybindings? I tried backslash, bslash, \, \\, but it didn't work. And the install guide only has a '~' example :(

Try <Control>backslash.........or better yet use the "Grab Keybinding" feature to let it capture your shortcut.

---

