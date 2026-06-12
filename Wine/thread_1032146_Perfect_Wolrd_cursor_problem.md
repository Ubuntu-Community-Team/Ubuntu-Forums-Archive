---
title: "Perfect Wolrd cursor problem"
date: 2009-01-06
forum: Wine
---

### Post by yuki_Michiyo on 2009-01-06
There's a cursor bug in PW and I've found a patch for wine 1.0.1 (the version I have) but i don't know what to do with it to make it work, where should I put it?
Here's the patch: [http://bugs.winehq.org/attachment.cgi?id=14380](http://bugs.winehq.org/attachment.cgi?id=14380)

---

### Post by AndrewRiedi on 2009-01-07
To use that patch, you must recompile Wine after applying it to the source.  I recently got another patch accepted into Wine that duplicated that functionality.  Just upgrade to Wine 1.1.11 (I guess 1.1.12 is bugged for some users) and there should be no need to apply it.  :)

There is a sticky at the top of this forum on where to get Wine 1.1.11.  Alternatively, you could just wait for 1.1.13.

PS: The .ani cursor patch was accepted into Wine 1.1.9, so any Wine at least as new as that should work w/o any other effort.

EDIT:
Upon checking the [AppDB]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=9923") entry for your program, it seems there is a regression in the Wine alpha builds (1.1.x) since 1.1.3.

Try [this]("http://wiki.winehq.org/Recommended_Packages") page for the packages needed to compile Wine if you want to try and go that route.  This [patch]("http://www.thehandofagony.com/alex/wine/patches/cursor-patches-1.1.2.patch") is written better and is what my code was based off of.  It says it is for 1.1.2, but with any luck it should apply to 1.0.1 just as well.  If not, just use the one you linked to.  If you need help with the actual compiling, etc. look on the Wine [wiki]("http://wiki.winehq.org") or let me know.

Good luck!

---

### Post by yuki_Michiyo on 2009-01-07
I found the 1.1.12 update and the cursor's just fine, but now there's another bug :( The armour won't show and the hair/eyes are white i googled it and it said it's called the naked bug (:D well they are naked afterall >.<) but i don't know how to fix it.

---

### Post by AndrewRiedi on 2009-01-07
Ok, did a little research for you.  :)

Seems the bug you are encountering is Wine [bug #12560]("http://bugs.winehq.org/show_bug.cgi?id=12560").

In the bug report there is a patch, but all the patch does is just tell WineD3D not to use a specific OpenGL extension.  Wine has support for disabling OpenGL extensions in the registry, so such a patch shouldn't be needed.

Open 'wine regedit' (from terminal, if needed) and make the following key:
HKCU/Software/Wine/OpenGL.  Then make the string value 'DisabledExtensions' and put 'GL_EXT_texture_compression_s3tc' as the string.  This should hopefully do what the patch in said bug report does.  I believe that registry keys are case-sensitive, so make sure you have the capital letters exactly like I have them.

Let me know if this works because, as I don't have the game and other people seem to use a patch instead, this is completely untested.

---

