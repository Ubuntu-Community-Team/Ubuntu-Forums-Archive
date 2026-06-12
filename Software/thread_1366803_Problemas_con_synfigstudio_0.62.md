---
title: "Problemas con synfigstudio 0.62"
date: 2009-12-28
forum: Software
---

### Post by guisheca on 2009-12-28
Que tal muchachos, necesito utilizar la ultima versión de este excelente programa de animaciones vectoriales y tengo un problema en ubuntu (digo ubuntu porque, por ejemplo, en arch me anda bien, pero quiero usarlo en el querido ubuntu).

El programa se ejecuta y abre a la perfección, el problema empieza cuando quiero dibujar algo: no aparece nada. Sin embargo las cosas se dibujan, sólo que no aparecen, puedo saberlo porque quedan registrados en el historial del menu de capas.

Lo ejecuté en un terminal y me aparece esto:

```
synfig(3795) [22:32:44] información: Cargando módulos desde /opt/synfig/etc/synfig_modules.cfg

** (synfigstudio:3795): CRITICAL **: murrine_style_draw_box_gap: assertion `height >= -1' failed

** (synfigstudio:3795): CRITICAL **: murrine_style_draw_box_gap: assertion `height >= -1' failed

** (synfigstudio:3795): CRITICAL **: murrine_style_draw_box_gap: assertion `height >= -1' failed

** (synfigstudio:3795): CRITICAL **: murrine_style_draw_box_gap: assertion `height >= -1' failed

** (synfigstudio:3795): CRITICAL **: murrine_style_draw_box_gap: assertion `height >= -1' failed

** (synfigstudio:3795): CRITICAL **: clearlooks_style_draw_box_gap: assertion `height >= -1' failed

** (synfigstudio:3795): CRITICAL **: clearlooks_style_draw_box_gap: assertion `height >= -1' failed

** (synfigstudio:3795): CRITICAL **: murrine_style_draw_box_gap: assertion `height >= -1' failed

** (synfigstudio:3795): CRITICAL **: murrine_style_draw_box_gap: assertion `height >= -1' failed

** (synfigstudio:3795): CRITICAL **: murrine_style_draw_box_gap: assertion `height >= -1' failed

** (synfigstudio:3795): CRITICAL **: murrine_style_draw_box_gap: assertion `height >= -1' failed

** (synfigstudio:3795): CRITICAL **: aurora_style_draw_box_gap: assertion `height >= -1' failed

** (synfigstudio:3795): CRITICAL **: aurora_style_draw_box_gap: assertion `height >= -1' failed

** (synfigstudio:3795): CRITICAL **: aurora_style_draw_box_gap: assertion `height >= -1' failed
```

El cambio entre murrine, aurora y clearlooks se produce al cambiar los engines en "apariencias", lo hice pensando que eso podría ser el problema pero no funcionó.

En fin, quisiera poder usar este genial programa en mi ubuntu, pero tengo este inconveniente.

Otro dato: la versión de repositorios (0.61) funciona a la perfección, pero quisiera poder usar la última puesto que muchos tutoriales están referidos a ésta. También compilé las fuentes pero me da el mismo error.

Saludos.

---

### Post by guisheca on 2009-12-31
Me choca a veces que los programas nativos de linux funcionen mejor en windows que en linux. Con la versión para win no tengo ningún drama...

---

### Post by eamusic on 2010-01-30
Hola Compañero Ubuntista

Te cuento que me estaba pasando lo mismo, hasta que decidí detener los efectos que tenía activados con el compiz y VOILA!!! todo de maravilla de nuevo con este espectacular programa.

Así mismo probé iniciar la shell de gnome 3 y también funcionó. Tal vez exista cierto problema de compatibilidad entre esos dos programas.

RECOMENDACIONES

1.Inicia una nueva sesión de usuario con ningún gestor de ventanas a excepción del que trae por defecto ubuntu.

2. Corre el programa Synfigstudio (desde terminal o desde el menú aplicaciones)

POR ÚLTIMO

Aquí están los datos de mi equipo donde ejecuto mis programas:

Distribución: UBUNTU 9.10 KARMIC KOALA
Entorno de Escritorio: GNOME 2.28  GNOME SHELL 3.0
Núcleo: Linux 2.6.31-17
Plataforma: x86_64
CPU: AMD Phenom 8650 Triple Core Processor
Memoria: 2G
Uso Compiz para los efectos de escritorio y Emerald como gestor de ventanas.


Espero te sirva de ayuda.
:popcorn:

---

