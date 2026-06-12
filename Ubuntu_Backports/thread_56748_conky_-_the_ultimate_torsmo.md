---
title: "conky - the ultimate torsmo"
date: 2005-08-13
forum: Ubuntu Backports
---

### Post by super on 2005-08-13
any chance of a backport for this app?  :???: 

it was a fork of torsmo but apparently torsmo is dead (or so i've heard)
it is actually a lot better than torsmo, and the debian dudes are gonna be adding it to their repos soon.

[this is the homepage](http://conky.sourceforge.net/)

---

### Post by cutOff on 2005-08-14
It seems pretty interesting.I second the motion.

---

### Post by jtan325 on 2005-08-31
just to let you guys know, conky 1.3.0 came out yesterday, big pimpin'. see [http://www.ubuntuforums.org/showthread.php?t=61297&highlight=conky](http://www.ubuntuforums.org/showthread.php?t=61297&highlight=conky)

---

### Post by SWAT on 2005-09-26
I also support this request. Seems like a VERY good program and far better than torsmo. When could this program be in the repositories? (an estimate?) 
> Torsmo is unmaintained, and it's recommended that you use Conky instead, which has many more features then torsmo. A lot of things which required external scripts with torsmo are built-in to Conky. [http://conky.sf.net/](http://conky.sf.net/)

---

### Post by strikeforce on 2005-09-27
Theres a debian package there already.  Just download it from there?

---

### Post by MetalMusicAddict on 2005-09-27
[QUOTE=strikeforce]Theres a debian package there already.  Just download it from there?[/QUOTE]
The .deb i386 works on Hoary. Just gotta figure out how to config the damn thing. Any help?

---

### Post by cfa on 2005-09-28
look at some exemple at 

[http://conky.sourceforge.net/screenshots.html](http://conky.sourceforge.net/screenshots.html)

> Here are some screenshots of Conky in action. Each screenshot comes with a linked conkyrc file and any other scripts that may be needed.

enjoy

---

### Post by cutOff on 2005-09-28
Hi all, good news for breezy users

$ sudo aptitude show conky
Paquete: conky
Nuevo: sí
Estado: instalado
Instalado automáticamente: no
Versión: 1.3.1-1
Prioridad: optional
Sección: universe/utils
Desarrollador: Jason Tan <jtan325@gmail.com>
Tamaño sin comprimir: 299k
Depende de: libc6 (>= 2.3.4-1), libice6, libsm6, libx11-6, libxext6
Descripción: highly configurable system monitor for X based on torsmo
 Conky is a system monitor for X originally based on the torsmo code. Since its
 original conception, Conky has changed a fair bit from its predecessor. Conky
 can display just about anything, either on your root desktop or in its own
 window. Conky has many built-in objects, as well as the ability to execute
 programs and scripts, then display the output from stdout. See
 [http://conky.sf.net](http://conky.sf.net) for more info.

---

