---
title: "[SOLVED] ASpell &amp;amp; PHP?"
date: 2008-10-21
forum: Server Platforms
---

### Post by angstsix on 2008-10-21
Hello, I'm trying to get Aspell running with php. but having some issues.

I ran this to install it:
apt-get install libgtkspell0 aspell aspell-en

but when I try to run the php code, I get this error:

Fatal error: Call to undefined function pspell_new()

I assume that i must link Aspell to PHP. but I can't seem to figure out how to do this. any ideas would be great!

thanks in advance for your time!
-Ken

---

### Post by angstsix on 2008-10-21
ok, i found the issue. i need to run this aswell:

apt-get install php5-pspell

reload php, and everythings working correctly.:)

---

