---
title: "whats is a retained package?"
date: 2005-03-10
forum: Ubuntu Backports
---

### Post by fabiang on 2005-03-10
Hi,

i'm doing an apt-get upgrade now, and i see this message:
> 
me@mymachine: ~$ sudo apt-get upgrade
Leyendo lista de paquetes... Hecho
Creando árbol de dependencias... Hecho
Los siguientes paquetes se han retenido: <------ LOOK HERE
  gftp-common gftp-gtk hotplug
Se actualizarán los siguientes paquetes:
  bogofilter cdrecord cpio cupsys cupsys-bsd cupsys-client debhelper emacs21
  emacs21-bin-common emacs21-common evolution gettext gettext-base gimp
  ...
 
¿What is a retained package, why this exists?

Thanks for your responses, when i'm reading you i was learned a lot.

---

### Post by DJ_Max on 2005-03-10
It was help back for a reason, in your case, because you have to run apt-get dist-upgrade to actually upgrade your kernel.

---

### Post by jdong on 2005-03-11
The english version of APT calls them "Held Back" packages:

The reason is that it's not just a simple replace-old-with-new update for those packages. Either a new package has to be installed, an existing package has to be removed, or another extra operation must be done before the upgrade can take place.

As already mentioned, you need to use "dist-upgrade" to tell APT to be more aggressive in updating.

---

### Post by Bou on 2005-12-28
[QUOTE=jdong]As already mentioned, you need to use "dist-upgrade" to tell APT to be more aggressive in updating.[/QUOTE]

Hi, I'm doing just that but the packages are still held back:

> david@frandavid100:~$ sudo apt-get dist-upgrade
Password:
Leyendo lista de paquetes... Hecho
Creando árbol de dependencias... Hecho
Calculando la actualización... Listo
Los siguientes paquetes se han retenido:
  gnome-cups-manager linux-image-386 linux-restricted-modules-386
0 actualizados, 0 se instalarán, 0 para eliminar y 3 no actualizados.
david@frandavid100:~$

Any ideas? :(

---

### Post by jdong on 2005-12-31
Try forcing apt-get on each package by typing in **sudo apt-get install PACKAGENAME** for each of the three.

This should be able to suggest what needs to be done for the packages to install.

Please attach a copy of that output, too, so that we can isolate the cause for these upgrade difficulties -- they shouldn't happen on the typical Ubuntu setup +/- popular repositories.

---

### Post by dolarsrg on 2006-10-15
The easy way to do this is with:

sudo aptitude dist-upgrade

Aptitude can solve this kind of dependences ;)

---

