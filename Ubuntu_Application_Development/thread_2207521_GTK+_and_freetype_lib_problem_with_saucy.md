---
title: "GTK+ and freetype lib problem with saucy?"
date: 2014-02-24
forum: Ubuntu Application Development
---

### Post by CliveMcCarthy on 2014-02-24
I recently upgraded to Saucy and code that used to compile and link is broken. From what I have read on the web there is a version incompatibility between the installed freetype lib and the one needed for GTK+ and Pango. I'm afraid I'm not that clear about what is the root cause of my issue. The linker emits the message "**undefined reference to FT_Get_Advance**" obviously it is unable to find the symbol in the lib. The GTK+ compiler command-line is a mystery to me: I'm just using the standard[B] 'pkg-config --libs gtk+-3.0'
[/B]
I have tried a variety of libs to no avail. I have another application that uses freetype which compiles and links just fine. I have third application that uses GTK+ (but not freetype)  it too compiles & links just fine. Attempting to use GTK+ **and** freetype2 doesn't :mad:

I hate this kind of problem... Help please.

---

### Post by CliveMcCarthy on 2014-02-24
I think I have solved the problem. If I force /usr/lib/i386-linux-gnu to precede any other library paths then things work OK. I shall have to check for other libfreetype.a or libfreetype.so that may have been picked up incorrectly.

---

