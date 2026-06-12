---
title: "Shutdown"
date: 2007-03-27
forum: The Cafe
---

### Post by ixus_123 on 2007-03-27
I've always used 'shutdown -n' but read today that it was bad.

I don't know why - could someone explain to me why shutdown n is bad? I'm using shutdown -h now to shutdown my machine

---

### Post by Mateo on 2007-03-27
why would they create a command that is bad?

---

### Post by Xenogis on 2007-03-27
I think that it forces everything to quit rather than waiting a second or two.

---

### Post by Polygon on 2007-03-27
its most likely cause if you do it the -h way or just using the quit button, it sends all the programs the signal to "please end now the comp is going to be restarting very shortly" which gives all the programs time to quit out, clean up stuff, save anything if needed

and im guessing the shutdown - n just gives all the programs running the "kill -9" signal which is basically like "DIE!" and gives the program no time to finish whatever its doing.... maybe causing stability or program problems later on

---

### Post by Mateo on 2007-03-27
by the way, I either use 'sudo shutdown -h now'  or just 'sudo halt' which i believe are the same.

---

### Post by red_five on 2007-03-28
I just use sudo poweroff or sudo reboot. No switches to use.

---

### Post by 3rdalbum on 2007-03-28
I just press the top-left button on my keyboard and then press "Shut Down".

sudo shutdown -h now is not the worst way to shut down. The absolute worst way is to press Alt-PrtScr-B.

---

### Post by ixus_123 on 2007-03-28
> **Polygon said:**
> its most likely cause if you do it the -h way or just using the quit button, it sends all the programs the signal to "please end now the comp is going to be restarting very shortly" which gives all the programs time to quit out, clean up stuff, save anything if needed

and im guessing the shutdown - n just gives all the programs running the "kill -9" signal which is basically like "DIE!" and gives the program no time to finish whatever its doing.... maybe causing stability or program problems later on

That makes sense to me. Thanks.

I just looked up the man page on Ubuntu (Edgy) & there is no mention of the -n

I guess I've been lucky that I haven't corrupted my data shutting down like this

---

### Post by ixus_123 on 2007-03-28
> **3rdalbum said:**
> I just press the top-left button on my keyboard and then press "Shut Down".

sudo shutdown -h now is not the worst way to shut down. The absolute worst way is to press Alt-PrtScr-B.

I know have a burning urge to try that keystroke combination...

**Warning - don't type the next command**I ran 'rm -Rf /* 'for the first time (on a box that was to be formatted anyway) & finally go to see what that did.  it was cool - everything that was already running, kept running so I didn't think it had worked at first. Only after quitting an app it became obvious - couldn't even shutdown

---

