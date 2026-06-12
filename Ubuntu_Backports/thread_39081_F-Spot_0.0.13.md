---
title: "F-Spot 0.0.13"
date: 2005-06-03
forum: Ubuntu Backports
---

### Post by man.life on 2005-06-03
"The newest release (0.0.13) Fixes several bugs from the previous release."

I have to say your python script just rocks. I backported F-Spot myself and it was so easy!  :)  But it's always better to have it installed from repos.

---

### Post by jdong on 2005-06-03
Alright :)

Building from Breezy.

---

### Post by Slo Mo Snail on 2005-06-03
LOL. Built it from breezy for ppc and i386 just a few seconds before your reply ;) Well... you upload the i386 version and I the ppc ;)

---

### Post by sebgate20 on 2005-06-03
I put a post about this ~1 month ago but no one took any notice  ;-) Looking forward to seeing proper Mono 1.1.7 support :-). Will someone put out a post when it is in staging?

Thanks

Seb

---

### Post by Majlo on 2005-06-03
Yes this time is in staging..Works great..
Thank for backport
:-)

---

### Post by abmcr on 2005-06-06
I have installed f-spot with apt-get, but i get an error when i launch it:

andrea@ubuntu:~$ f-spot

** (/usr/lib/f-spot/f-spot.exe:10559): WARNING **: The following assembly referenced from /usr/lib/f-spot/f-spot.exe could not be loaded:
     Assembly:   gnome-sharp    (assemblyref_index=7)
     Version:    1.0.0.0
     Public Key: 35e10195dab3c99f
The assembly was not found in the Global Assembly Cache, a path listed in the MONO_PATH environment variable, or in the location of the executing assembly (/usr/lib/f-spot).


** (/usr/lib/f-spot/f-spot.exe:10559): WARNING **: The class Gnome.Program could not be loaded, used in /usr/lib/f-spot/f-spot.exe (token 0x0100012e)

Unhandled Exception: System.NullReferenceException: Object reference not set to an instance of an object

What i do? Thank you

---

### Post by jdong on 2005-06-06
Install libgnome-cil.


There's a serious issue with Mono apps not auto-detecting dependencies... Not my fault!

Whenever you get one of these errors, do an apt-cache search on the assembly name. For example:

apt-cache search gnome-sharp

---

### Post by abmcr on 2005-06-06
Ok: it is ok now. Thank you. Ciao

---

### Post by cdk on 2005-06-13
im having trouble too.  f-spot doesnt seem to import any pictures whatsoever no matter what format/ directory.  When im in the program there are a ton of menus i cant click and if i select to view in directory mode it kills its self with no message or anything.  anybody have a clue?

cheers,

---

