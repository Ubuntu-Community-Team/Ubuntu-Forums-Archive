---
title: "i cant hear what i am playing."
date: 2009-10-31
forum: Ubuntu Studio
---

### Post by Cool Surfer on 2009-10-31
Hi all

hi all i am using latest  ubuntu 9.10  and audacity 1.39 
.

When i record my guitar sound, it records but i cant hear what i am playing.

How can i hear what i amplaying .

thanks

---

### Post by Cool Surfer on 2009-11-01
Any help pl... I need to fix this soon, or I revert back to windows 7 ultimate edition :)
Everything works great win windows.

---

### Post by AutoStatic on 2009-11-01
Hello Cool Surfer, could you post a screenshot of the Audio I/O preferences window in Audacity?

---

### Post by Cool Surfer on 2009-11-01
thanks for replying....
here are the screen shots

---

### Post by AutoStatic on 2009-11-01
Thanks, but a Take a Screenshot window is on top of all the Audacity windows, could you post new ones without another Take a Screenshot window open?

---

### Post by Cool Surfer on 2009-11-01
sorry ..... lol

---

### Post by hansdown on 2009-11-01
Hi Cool Surfer.

You need to change the "grab after delay of" box to something like 3 seconds, or it will block your window with the screenshot window.

---

### Post by Cool Surfer on 2009-11-01
the above are screen shots i took again....

---

### Post by AutoStatic on 2009-11-02
Thanks for reposting! You could try enabling Software Playthrough in the Recording window.

---

### Post by moulden2 on 2009-11-02
I had a similar problem after a fresh install of 9.10.  Apparently my Line In was muted by default so I had to unmute it.  I suppose you could do this through terminal using alsa mixer but I was lazy and got "Gnome Alsa Mixer" off the software center.

---

### Post by Cool Surfer on 2009-11-02
Software playthro freezes the window and nothing happens.

Without playthro, it records fine, i can replay what i played on guitar fine, good quality, but i wan  to be able to hear what i am playing, while i am playing.....

---

### Post by AutoStatic on 2009-11-02
Maybe you could try something like Qtractor. Audacity is okay to edit stuff but it's no real good recording software.

---

### Post by RaumTrug on 2009-11-06
the problem could be that your soundcard is not set up for monitoring inputs. try to get some alsa mixer, the console one or better the gtk stuff mentioned above and enable/pull up the slider of the right device for the channel you're recording on (line or mic). also disable any other recording option than the channel you record on! you should be able to hear what's comming in your line, even when audacity is not running at all!!

in case you use different sound devices for recording and playback (say an usb guitar plug / usb mic, and want to hear sound on speakers from onboard or whatever soundcard) then things aren't so easy! you could check out jack, but it seems broken for record-only devices (like those usb-plugs/mics) at the moment; I was having problems with this, and fixing it isn't trivial.

---

