---
title: "[SOLVED] Error en Kubuntu"
date: 2008-09-30
forum: Software
---

### Post by ramiro_md on 2008-09-30
Gente hoy a la tarde instale kde 4.1..tiodo andaba joya hasta el primer reinició donde al iniciar el escritorio me salio un cartel de horror :S que decía lo siguiente:

Ha ocurrido un error fatal
The application Área de trabajo de Plasma (plasma) crashed and caused the signal 11 (SIGSEGV).
Please help us improve the software you use by filing a report at [http://bugs.kde.org](http://bugs.kde.org). Useful details include how to reproduce the error, documents that were loaded, etc.

Error fatal !!! :confused: me hace acordar a windows, otra vez no por favor :( xD

LO raro, es que no toque casi nada en el sistema ni en las preferencias como para que me tire un error tan "prematuramente". A propósito, el escritorio se queda en negro, el panel no carga y solo puedo ver el cairo-dock.

Un saludo.

---

### Post by Hei Ku on 2008-09-30
eso es porque el error fue justamente en Plasma, que maneja el escritorio.
Y 4.1 no esta apuntado a usuarios finales, asi q a reportar el error y apechugar.
Seguramente podes iniciarlo de vuelta corriendo plasma desde el Alt+F2.

---

### Post by ramiro_md on 2008-09-30
Lo solucioné, sin rpeortar byugs ni nada por el estilo..googleando y rompiendome el marote con el inglés lol.
EN una consola desde gnome puse lo siguientes códigos:

```
sudo aptitude install kdesu
```
```
rm -rf ~/.kde4
```
```
rm -rf in the /home/usuario/.kde4 directory
```

Después pude vovler a usar kde 4.1 :D

PD: Gracias a un amigo de la facu por el aguante xD.

---

