---
title: "Aeolus crashing"
date: 2017-03-18
forum: Ubuntu Studio
---

### Post by eric-wurbel on 2017-03-18
Hello,

I have exactly the same problem : Instant crash of aeolus.

At this time I have :
copied the stops directory somewhere in my home (/home/eric/Musique/Aeolus/stops).
Created a .aeolusrc in my home directory, and edited it so now it contains :
```

-J -S /home/eric/Musique/Aeolus/stops

```

-J tells aeolus to use jack
-S /home/... locates the stops directory

Note that this particular configuration has no influence on the crash : running aeolus "out of the box" provides exactly the same result.

The crash seems to be related to font manipulation (you screen capture mentions FT_Load_Glyph(), which is a function from the FreeType library. Is suspect that a font package update creates the error, but I don't know which one...

I'll try to investigate (perhaps asking to aeolus developpers).

Anybody any idea ?

regards

Eric

---

### Post by QIII on 2017-03-18
Moved to its own thread from [https://ubuntuforums.org/showthread.php?t=2352819](https://ubuntuforums.org/showthread.php?t=2352819)

While your symptoms my be very similar, the underlying cause might be vastly different.  Also, the OP of the other thread deserves individual attention for his/her question and do you.

---

