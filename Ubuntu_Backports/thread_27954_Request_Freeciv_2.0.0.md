---
title: "Request: Freeciv 2.0.0"
date: 2005-04-18
forum: Ubuntu Backports
---

### Post by Gustav on 2005-04-18
Freeciv 2.0.0 is finally out. :grin: 

Having this as a backport would make the world a better place.

[http://www.freeciv.org](http://www.freeciv.org)

---

### Post by MaX on 2005-04-20
[QUOTE=Gustav]Freeciv 2.0.0 is finally out. :grin: 

Having this as a backport would make the world a better place.

[http://www.freeciv.org](http://www.freeciv.org)[/QUOTE]

It's in Debian Experimental now so it shouldn't be that long now should it?

BTW Is the SDL version finnished

---

### Post by skoal on 2005-04-20
No more beta.  Sweet...

Time to get my Stealth bombers destroyed by some AI archer shooting bows and arrows out of fortified city walls.  What's up with that?  A good game though.  A must play for anyone who likes the board game Risk.

---

### Post by pkarlos_76 on 2005-04-24
[QUOTE=MaX]It's in Debian Experimental now so it shouldn't be that long now should it?

BTW Is the SDL version finnished[/QUOTE]

Looks like we need a library backported too for freeciv 2.0.0, I haven't determined yet what dependancies that version of of lib may need though either.  :roll: 

Unpacking freeciv-client-gtk (from freeciv-client-gtk_2.0.0-1_i386.deb) ...
dpkg: dependency problems prevent configuration of freeciv-client-gtk:
 freeciv-client-gtk depends on libsdl-mixer1.2 (>= 1.2.6); however:
  Version of libsdl-mixer1.2 on system is 1.2.5-9.
dpkg: error processing freeciv-client-gtk (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 freeciv-client-gtk

---

### Post by Gustav on 2005-04-25
[QUOTE=pkarlos_76]Looks like we need a library backported too for freeciv 2.0.0, I haven't determined yet what dependancies that version of of lib may need though either.  :roll: 

Unpacking freeciv-client-gtk (from freeciv-client-gtk_2.0.0-1_i386.deb) ...
dpkg: dependency problems prevent configuration of freeciv-client-gtk:
 freeciv-client-gtk depends on libsdl-mixer1.2 (>= 1.2.6); however:
  Version of libsdl-mixer1.2 on system is 1.2.5-9.
dpkg: error processing freeciv-client-gtk (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 freeciv-client-gtk[/QUOTE]
 It still seems to work though, with sound and everything.

(if there's something that doesn't work I didn't notice it)

And libsdl-mixer1.2 v 1.2.6 doesn't have any unfulfilled dependencies so that's no problem (well the libsdl-mixer1.2-dev have to be updated to if you have that).

---

### Post by Gustav on 2005-04-28
Version 2.0.1 is out now. It has some bugfixes and translation updates. 

Debs can be found at [http://ftp.debian.org/debian/pool/main/f/freeciv/](http://ftp.debian.org/debian/pool/main/f/freeciv/)

---

### Post by fromoze on 2005-04-28
I've done amd64 hoary packages... but no-sound package. I don't know if it's normal to didn't have this package :?

---

### Post by MaX on 2005-04-30
[QUOTE=Gustav]Version 2.0.1 is out now. It has some bugfixes and translation updates. 

Debs can be found at [http://ftp.debian.org/debian/pool/main/f/freeciv/](http://ftp.debian.org/debian/pool/main/f/freeciv/)[/QUOTE]
 Anything happening on the backport front?

---

### Post by jdong on 2005-04-30
grabbing it now.

---

### Post by Gustav on 2005-05-03
[QUOTE=jdong]grabbing it now.[/QUOTE]
 wonderful!!!

---

