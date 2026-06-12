---
title: "WoW doesn't start"
date: 2010-10-17
forum: Wine
---

### Post by shawnic on 2010-10-17
I've been looking around for the past few days and can't find anyone with a similar problem, so I hope someone can help me because I have no idea what could be wrong.

Since I installed the newest patch for Cataclysm, Wow doesn't open correctly.
The launcher works but when I click play, the launcher closes and nothing else happens.
If I run Wow.exe directly it starts to open and then quits.
once or twice Wow.exe has appeared in the system monitor but it says it's sleeping and still doesn't open.

I'm not getting any error messages or any other confirmation that it's broken in any way, it's just not opening.

Any ideas?

---

### Post by apostra on 2010-10-17
Hey mate,

Would be better if you start it on terminal, to get a clue for the errors.

Do you run it at opengl? What Graphic card do you have and what are drivers installed?

Is it done the installation? Using cata installer, you can play while you download. This may cause some crashes and errors. In general cata installer must be buggie a bit. I did twice installation. Somehow, the new installer at some point freezes, lose connection and starts all over again.

---

### Post by shawnic on 2010-10-17
```
X Error of failed request:  GLXBadDrawable
  Major opcode of failed request:  135 (GLX)
  Minor opcode of failed request:  5 (X_GLXMakeCurrent)
  Serial number of failed request:  205
  Current serial number in output stream:  205

```

i get the same problem and error whether i run in opengl or not.
i have an NVIDIA GeForce 7050 and i think the driver version is 173

All the patches were completely finished when i attempted to play.

---

### Post by apostra on 2010-10-18
Hey mate,

what version of wine you got? 

I did a google search and find that is mostly a driver bug. You might need to re-install graphics drivers from scratch or is some dlls missing from wine, somehow. I could be wrong ofc.

Although I am not 100% sure. I would advice do a google search with terminal errors and you will see some suggestions. The most of them solved with re-installing of graphics drivers and wine. 

Apologies for not  giving any suggestions, never faced this error myself, so I cant be 100% sure for solution. 

Best Luck mate.

---

