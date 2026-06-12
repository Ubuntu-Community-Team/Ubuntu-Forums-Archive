---
title: "Iconos en menu&gt;sistema  ...para compartir"
date: 2009-11-22
forum: Software
---

### Post by Sleeping Beauty on 2009-11-22
Hola a tod@s! No sé si notaron que por defecto en KK no aparecen íconos en el menú de Sistema (es decir los de >preferencias, >administración, >ayuda, >Acerca de GNOME, >Acerca de Ubuntu)
Para los que como yo, no tienen idea de como hacer que aparezcan, les dejo una simple linea de consola que mágicamente los hace visibles... ya sé que para los que saben es una pavada pero me pareció bueno ahorrarle a muchos el trabajo de buscarlo ;)
$ gconftool-2 --type Boolean --set /desktop/gnome/interface/menus_have_icons True

---

### Post by santiagoward2000 on 2009-11-22
> **Sleeping Beauty said:**
> Hola a tod@s! No sé si notaron que por defecto en KK no aparecen íconos en el menú de Sistema (es decir los de >preferencias, >administración, >ayuda, >Acerca de GNOME, >Acerca de Ubuntu)
Para los que como yo, no tienen idea de como hacer que aparezcan, les dejo una simple linea de consola que mágicamente los hace visibles... ya sé que para los que saben es una pavada pero me pareció bueno ahorrarle a muchos el trabajo de buscarlo ;)
$ gconftool-2 --type Boolean --set /desktop/gnome/interface/menus_have_icons True

Hola!
Por si alguno le tiene miedo a la consola, tambien se pueden activar yendo a **Sistema > Preferencias > Apariencia**, y activando **Mostrar iconos en los menues** bajo la pestaña **Interfaz**.
Saludos!

---

