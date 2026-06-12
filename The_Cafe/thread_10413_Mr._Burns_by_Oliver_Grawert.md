---
title: "Mr. Burns by Oliver Grawert"
date: 2005-01-07
forum: The Cafe
---

### Post by rbrimhall on 2005-01-07
Anybody tested this out yet?

[http://www.grawert.net/software/mrburns/](http://www.grawert.net/software/mrburns/)

Seems like the most efficient CD burner for audio yet... since nautlius can handle almost all other burning tasks... plus it uses hal instead of cdrecord for device detection.

---

### Post by Dylanby on 2005-01-07
Looks like it might be worthwhile.
Easy too since he's supplied Ubuntu deb's. Thanks for the heads up.

Seems like a **lot** of Gnome based burning apps are in development right now.

There's also Coaster ([http://www.coaster-burn.org](http://www.coaster-burn.org)) which is based on libburn. Which is hosted by (aack, my bad) the Freedesktop project. I'm going to try that one out too.

---

### Post by rider343 on 2005-01-07
Graveman works fine

---

### Post by rbrimhall on 2005-01-07
Graveman looks good... if it would only detect my writer... cdrecord --scanbus is hit and miss with 2.6 kernels still.

---

### Post by ow50 on 2005-01-07
All the gnome cd burning apps i have tried have the same problem: they don't auto-detect my burner and don't allow me to specify it myself. Same problem with mr.burns.

---

### Post by rbrimhall on 2005-01-07
really? 'cause if nautilus cd burner works so should mr. burns... it uses hal and dbus to get your burner. The gnomebaker package from here picked my burner up from gconf:

[http://people.debian.org/~goedson/debian/packages/gnomebaker/snapshots/](http://people.debian.org/~goedson/debian/packages/gnomebaker/snapshots/)

It's a debian deb so it'll complain about the gnome-vfs ubuntu version but it installs anyway and runs fine... even picked up my writer for a change ;)

---

### Post by Lovechild on 2005-01-07
Mr. Burns.. is the author fishing for a Simpsons fan like myself to say "Excellent" ?

---

### Post by daniels on 2005-01-07
libburn is not 'part of the [f]reedesktop project' as such; we merely host its development, as we do many other projects.

-d, with his fd.o hat on

---

### Post by ow50 on 2005-01-07
[QUOTE=rbrimhall]really? 'cause if nautilus cd burner works so should mr. burns... it uses hal and dbus to get your burner. The gnomebaker package from here picked my burner up from gconf:

[http://people.debian.org/~goedson/debian/packages/gnomebaker/snapshots/](http://people.debian.org/~goedson/debian/packages/gnomebaker/snapshots/)

It's a debian deb so it'll complain about the gnome-vfs ubuntu version but it installs anyway and runs fine... even picked up my writer for a change ;)[/QUOTE]

Thanks for the link. Gnomebaker finally recognizes both my cd drives. Version 0.2 didn't.

I compiled it from source to avoid the complaints about a broken package and it works smooth.

---

### Post by freduardo on 2005-01-08
[QUOTE=Lovechild]Mr. Burns.. is the author fishing for a Simpsons fan like myself to say "Excellent" ?[/QUOTE]
let's hope its not "exactly....doh!"  ;) 

anyway was looking for a good burning tool for ubuntu
gonna give this one a try

---

### Post by lee_connell on 2005-01-09
[QUOTE=ow50]Thanks for the link. Gnomebaker finally recognizes both my cd drives. Version 0.2 didn't.

I compiled it from source to avoid the complaints about a broken package and it works smooth.[/QUOTE]


hey can you give me a hand compiling gnome baker, coaster as it needs gthread-2.0, where do i get that?

Lee

---

### Post by ow50 on 2005-01-09
[QUOTE=lee_connell]hey can you give me a hand compiling gnome baker, coaster as it needs gthread-2.0, where do i get that?[/QUOTE]
gthread-2.0 seems to be a part of libglib-2.0. Just apt-get it.

Coaster i haven't compiled. The depencies seemed so scary that i didn't care to bother trying to get them.

---

### Post by lee_connell on 2005-01-09
gnomebaker is really nice!~   btw: i have libglib-2.0 and it still complains about gthread so maybe i need to tell it where....

---

### Post by Johan on 2005-01-09
You might need a -dev version installed as well to make it past ./configure.

---

### Post by rbrimhall on 2005-01-09
I can email you a deb of gnomebaker that I made with checkinstall if you send me an email.

---

### Post by lee_connell on 2005-01-09
[http://people.debian.org/~goedson/debian/packages/gnomebaker/snapshots/](http://people.debian.org/~goedson/debian/packages/gnomebaker/snapshots/) is where i got gnomebaker.

I wanna try coaster now to see what it's got.


Johan: that's what it was i needed the -dev version. but i failed to meet all dependencies when it hit bakery-2.4 as 2.3.8 is only available in the repos :(

Lee

---

