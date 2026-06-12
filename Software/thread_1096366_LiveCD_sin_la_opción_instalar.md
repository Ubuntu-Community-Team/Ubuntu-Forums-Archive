---
title: "LiveCD sin la opción instalar"
date: 2009-03-14
forum: Software
---

### Post by carcar8 on 2009-03-14
Hola, Salu2 a todos

Se puede crear un LiveCD de Ubuntu con la opción de instalación desactivada?

Que arranque el sistema Ubuntu desde el CD, pero que no aparezca Instalar.

Carcar8
%%%%%%%

---

### Post by pablo.s on 2009-03-14
Teoricamente se puede, **si querés hacer el intento** te aconsejo instalar uck (utilidad para remasterizar imagenes .ISO). Después supongamos que abris la ISO de Intrepid y le configurás que no le ponga ubiquity ni ubiquity-frontend-gtk.
Probás la imagen remasterizada y si es lo que querias, muy bien diez.

OJO: como es algo que **nunca probé**, es una **sugerencia** y **no garantizo resultados**.

Saludos nuevamente y avisá si funciona.

---

### Post by Hei Ku on 2009-03-14
Aca tenes una pagina que explica como personalizar el LiveCD.
[https://help.ubuntu.com/community/LiveCDCustomization](https://help.ubuntu.com/community/LiveCDCustomization)

---

### Post by pablo.s on 2009-03-16
Ayer probé con el método que decia antes. Me puse a probar con Uck el tema de remasterizar la ISO de Jaunty Alpha 6 que tenia guardada.
Primero monta la imagen, la descomprime y la desmonta. Luego monta el sistema de ficheros Squash y lo descomprime. Todo esto ocupa unos 5 GB de disco y un rato largo. A partir de ahi te pide configurar el idioma de instalación, el idioma del escritorio, los paquetes que querés agregar o borrar (yo le retiré compiz, open office, brasero, ekiga, rhythmbox y evolution) para hacer la imagen mas completa o mas austera. De hecho le iba a retirar tambien ubiquity para probar si asi le capaba la instalación, pero me di cuenta tarde.
Al final se toma otro rato más para componer la ISO y cuando finaliza el proceso estamos listos para probarla. Anda bien, lo recomiendo a los que quieran armarse una imagen personalizada para regalar, o bien para armar algún proyecto con sus aplicaciones favoritas y poder mostrarlas en modo live.
Saludos.

---

