---
title: "Uh-oh. I think I burned up my video card"
date: 2006-04-24
forum: The Cafe
---

### Post by K.Mandla on 2006-04-24
I wasn't really cranking it. I was editing a text file when the screen melted to off-white, slowing near the corners. Now it only gives me red and green streaks when I power it up. Not even a BIOS screen. :(

Methinks it's dead. Anyone care to second my diagnosis? :-k

---

### Post by Wallakoala on 2006-04-24
Sounds pretty bad...

It might be not be your video card. It could be anything in your computer theoretically

---

### Post by Iandefor on 2006-04-24
Sounds like a monitor problem to me. Have you verified that it isn't the monitor?

---

### Post by benplaut on 2006-04-24
aye, sounds like the moniter

---

### Post by PatrickMay16 on 2006-04-24
Sounds more like the monitor than the video card. Though if it does turn out to be the video card, was it an ATI video card? If so, then that's not so much of a loss. Perfect opportunity to get something superior (ie: made by Nvidia)

---

### Post by wbeck85 on 2006-04-24
Nice, Patrick, nice.   :)

---

### Post by dmacdonald111 on 2006-04-24
Silly suggestion I know, but you haven't got any powerful speakers nearby?

---

### Post by K.Mandla on 2006-04-24
Well, I'm 99.9 percent sure it was the video card now. The LCD works fine. It was a GeForce 4 Go 440 in an Inspiron 8000, and when I swapped it out for the old Geforce2, it worked again. I'm typing on it now. 

I don't know if it got too hot or if it's fried permanently, but I'll troubleshoot it later and see if it's something that can be resurrected.

There's no chance this is a driver or software issue, is there? I've been tinkering with XFCE under Dapper, and I was getting video freezeups before this happened while messing with the composite manager. Would using an incorrect driver cause a lockup like that?

---

### Post by benplaut on 2006-04-24
nah, doesn't sound like drivers...

now go out and get yourself a decent 6600gt ;)

---

### Post by K.Mandla on 2006-04-24
:D Soon, soon. ...

---

### Post by wmcbrine on 2006-04-24
[QUOTE=PatrickMay16]Sounds more like the monitor than the video card. Though if it does turn out to be the video card, was it an ATI video card? If so, then that's not so much of a loss. Perfect opportunity to get something superior (ie: made by Nvidia)[/QUOTE]
ATI this, Nvidia that... bah. Nothing yet can replace my Matrox G400.

---

### Post by K.Mandla on 2006-04-25
Okay, now this is weird: I put the GeForce4 back into the laptop, just as a testing measure, and now it seems to be fine again. I'm not sure what to think. 

It's a definite video card issue, since the GeForce2 worked fine. I'm guessing it just overheated? I know I've been tampering with the xorg.conf file, and I know I tinkered with it again when I put the GeForce2 in there ... is there really no way that this could be a software configuration problem or a driver issue? Did I pick a configuration that caused it to freak out?

Sigh. The wonders of technology.

---

### Post by henriquemaia on 2006-04-25
[QUOTE=K.Mandla]Okay, now this is weird: I put the GeForce4 back into the laptop, just as a testing measure, and now it seems to be fine again. I'm not sure what to think. 

It's a definite video card issue, since the GeForce2 worked fine. I'm guessing it just overheated? I know I've been tampering with the xorg.conf file, and I know I tinkered with it again when I put the GeForce2 in there ... is there really no way that this could be a software configuration problem or a driver issue? Did I pick a configuration that caused it to freak out?

Sigh. The wonders of technology.[/QUOTE]

Test it, stressing it, loading lots of gl apps and see if it gets excessibly hot.

---

### Post by Jason_25 on 2006-04-25
So you are exchanging video cards in a laptop?  Maybe the connection is loose and when it heats up it loses contact?  Or maybe it could be as simple as corroded connectors?

---

### Post by K.Mandla on 2006-04-25
[QUOTE=Jason_25]So you are exchanging video cards in a laptop?  Maybe the connection is loose and when it heats up it loses contact?  Or maybe it could be as simple as corroded connectors?[/QUOTE]
I suppose that's possible, but would I get screen lockups and a fade to white if it was just a connection? This is a slow, melting effect starting at the center and working its way up to the top corners ... which again, is why I suspected a burned-up video card. It's very creepy. And before that, I had weird desktop freezes. Of course, now, everything is five-by.

[QUOTE=henriquemaia]Test it, stressing it, loading lots of gl apps and see if it gets excessibly hot.[/QUOTE]
Good call. I think I'll build an XGL desktop and see if I can get it to melt down again. I still have the original GeForce2, so if it goes out again, I can still get things working.

By the way, thanks to all who helped. You guys (and gals) are what make this forum great. Cheers! :mrgreen:

---

