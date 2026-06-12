---
title: "Unnecessary dependencies ?"
date: 2005-11-15
forum: Repositories &amp; Backports
---

### Post by kabus on 2005-11-15
I have recently installed the Mutt email client, and for some reason it depends on Postfix, which I don't need because I prefer other MTAs.
Trying to apt-get remove postfix also uninstalls Mutt, of course.

Could this be considered a bug and should I report it somewhere to get it changed, or are there good reasons for this dependency and I shouldn't waste people's time moaning about it ? :smile: 

Is there a way to make apt-get ignore dependencies ?

---

### Post by brim4brim on 2005-11-15
Well if Mutt has Postfix as a dependency it may need it for certain features.  Just because you don't use those features does not mean that it's safe to remove the package because the program may check for them at startup or you may use them at some stage in the future and then wonder why Mutt is performing oddly or in other words I'd assume it's to protect the user from themselves and the lesser of two evils to have an unused package rather than leaving a program in a position where a user might use a feature that would crash it or remove a package that would stop some of there apps from working properly.

---

### Post by kabus on 2005-11-15
[QUOTE=brim4brim]Well if Mutt has Postfix as a dependency it may need it for certain features. [/QUOTE]

I just checked the tar on mutt.org and the only real dependency seems to be the ncurses library.
I also installed it on Arch Linux, where it doesn't depend on Postfix.:confused: 

Oh well, I guess it's no big deal having Postfix lying around doing nothing. :smile:

---

