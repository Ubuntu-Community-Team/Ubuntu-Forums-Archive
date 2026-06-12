---
title: "backports repository is not working for me"
date: 2005-03-05
forum: Ubuntu Backports
---

### Post by fabiang on 2005-03-05
Hi,

First the first: my sources.list
> 
# ...
#proyecto backports
deb [http://backports.ubuntuforums.org/backports](http://backports.ubuntuforums.org/backports) warty-backports main universe multiverse restricted
deb [http://backports.ubuntuforums.org/backports](http://backports.ubuntuforums.org/backports) warty-extras main universe multiverse restricted
#...


For example in a post you say:
Warty backport: Firefox 1.0 with 1.0.0+dfsg.1-6ubuntu1~4.10ubp1 

i do:
> 
$ sudo apt-get update
$ sudo apt-get install mozilla-firefox


and apt says me:
> 
Leyendo lista de paquetes... Hecho
Creando árbol de dependencias... Hecho
mozilla-firefox ya está en su versión más reciente.
0 actualizados, 0 se instalarán, 0 para eliminar y 111 no actualizados.

In english: you have the last version of mozilla-firefox

Well, finally i really have this version: 
> 
Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.7.5) 
Gecko/20041209 Firefox/1.0 (Ubuntu)
(Ubuntu package 1.0-2ubuntu4-warty99)

And i see 1.0-2ubuntu4-warty99 != 1.0.0+dfsg.1-6ubuntu1~4.10ubp1 

The same thing with:
- gaim you say gaim 1.1.2 it's here and i have only 1.1.1
- and others...

One last question: ¿what's staging?

---

### Post by kassetra on 2005-03-05
[QUOTE=fabiang]One last question: ¿what's staging?[/QUOTE]

Staging is where those versions are that you are not getting.  Staging means "not ready to be called stable" ... 

If you want those versions you'll need to add:
deb [http://backports.ubuntuforums.org/backports/](http://backports.ubuntuforums.org/backports/) warty-backports-staging main universe restricted multiverse

to your sources.list and then click on Reload in synaptic or do apt-get update.

---

### Post by jdong on 2005-03-07
The versions you're talking about (Firefox 1.0+dfsg, gaim 1.1.2) are still relatively experimental/new, and are in the staging area.

There's known issues with Firefox 1.0.0 and locales. GAIM depends on a new glib that seems to be causing menu hell.

Both are being worked on at the moment.

---

