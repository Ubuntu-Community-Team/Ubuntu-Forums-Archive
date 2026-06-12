---
title: "TF2 caudiosourcememwave"
date: 2009-09-02
forum: Wine
---

### Post by andrew13321 on 2009-09-02
I get an error with Wine under TF2. It's kind of like this:
```
caudiosourcememwave
```
TF2 then crashes after I get the error.  I have a Soundblaster XFI card.

---

### Post by sherl0k on 2009-09-02
Remove PulseAudio. I couldn't get TF2 working until I did that. Wine/CXGames doesn't support it, and only causes problems with games.

---

### Post by andrew13321 on 2009-09-02
PulseAudio has been gone for a long time...

---

### Post by sherl0k on 2009-09-02
run with -dxlevel 80

if that works, try -dxlevel 81

then -dxlevel 9

---

### Post by andrew13321 on 2009-09-02
Isn't that a major downgrade, and where do I run it?

---

### Post by sherl0k on 2009-09-03
right click TF under the My Games tab, click "Properties" and then "Set launch options." I also have -console -novid in there also.

---

### Post by andrew13321 on 2009-09-03
It still isn't working.
I've also noticed it's in other games too. Zombie Panic! Source gets the .wav error to.

---

